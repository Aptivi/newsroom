+++
date = '2026-04-02T08:28:49Z'
title = 'How Nitrocid Manages Threads?'
+++

When Nitrocid introduced the thread management feature for the first time, it was made as a solution to a problem that plagued System.Threading.Thread when it comes to [`Interrupt()`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.interrupt?view=net-10.0#system-threading-thread-interrupt) and then starting the thread again. When the thread is finally interrupted or terminated either automatically or by `Interrupt()`, the thread state, which [`ThreadState`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.threadstate?view=net-10.0) manages, goes to `Stopped`, which means that [`Start()`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.start?view=net-10.0#remarks) won't work again, as mentioned in the Remarks section:

> Once the thread terminates, it cannot be restarted with another call to `Start`.

The solution to this problem is to create a new instance of the thread again with the same target function then starting it again, if you want to restart the same thread. However, this means that you'll have to update all constructors, should the function name and/or signature or the thread name change, and inconsistencies in the parameter construction may show, depending on the size of the codebase.

As a result, we have made a class in Nitrocid, called [`KernelThread`](https://github.com/Aptivi/Nitrocid/blob/2153036914d6259ba04ef5852a775f6041ad0d33/public/Nitrocid.Base/Kernel/Threading/KernelThread.cs), that abstracts away the solution to this problem in a single function.

## The solution

The solution to the above problem is to introduce a new class that manages a single `Thread` class and its parameters, called `KernelThread`, which is named appropriately in Nitrocid's base library.

When you create a kernel thread class, the thread that this class manages gets created with the provided constructor parameters, which are:

* **Thread name**: Name of the thread that this class stores for each thread class (re)generation
* **Background**: Whether this thread is part of the background or the foreground
* **Executor**: Either a single function or a function with one object that contains thread parameters

The constructor makes a new `Thread` class, sets up nested thread parameters (if any), and marks the `KernelThread` as ready, evidenced by `isReady` being true. You can verify the readiness of the thread by checking `IsReady`.

When `Start()` is called, the thread starts under the following conditions:

* If the thread is ready to start (that is, `IsReady` is `true`). An exception will be thrown if otherwise.
* If the thread state is not `ThreadState.Stopped`. The thread doesn't start if otherwise.
* If the thread is not already running (that is, `IsAlive` is `false`). The thread doesn't start if otherwise.

This is all done under the following code (debugging code excluded):

```csharp
public void Start()
{
    if (!IsReady)
        throw new KernelException(KernelExceptionType.ThreadNotReadyYet);
    if (BaseThread.ThreadState.HasFlag(ThreadState.Stopped) || IsAlive)
        return;

    BaseThread.Start();
    StartChildThreads(null);
}
```

Here's when we come to the solution to the thread restarting problem. As we know that `Thread` can't restart the thread if the thread has been stopped either automatically or by `Interrupt()`, the `Stop()` function has been made to abstract away the need of regenerating the thread class with the same (and consistent) parameters once Nitrocid stops the `KernelThread`.

```csharp
public void Stop() =>
    Stop(true);
```

The above function implies that Nitrocid is required to regenerate the kernel thread, but you can pass `false` to tell it not to regenerate the thread once the function stops. Here's what this function does (debugging code included):

```csharp
public void Stop(bool regen)
{
    try
    {
        DebugWriter.WriteDebug(DebugLevel.I, "Stopping kernel thread {0} with ID {1}", vars: [Name, ThreadId]);
        isStopping = true;
        BaseThread.Interrupt();
        DebugWriter.WriteDebug(DebugLevel.I, "Stopping child threads for kernel thread {0} with ID {1}", vars: [Name, ThreadId]);
        StopChildThreads();
        if (!Wait(60000))
            DebugWriter.WriteDebug(DebugLevel.W, "Either the parent thread or the child thread timed out for 60000 ms waiting for it to stop");
        isReady = false;
        DebugWriter.WriteDebug(DebugLevel.I, "Finished with regen {0}", vars: [regen]);
        if (regen)
            Regen();
    }
    catch (Exception ex) when (ex.GetType().Name != nameof(ThreadInterruptedException) && ex.GetType().Name != nameof(ThreadStateException))
    {
        DebugWriter.WriteDebug(DebugLevel.I, "Can't stop the kernel thread: {0}", vars: [ex.Message]);
        DebugWriter.WriteDebugStackTrace(ex);
    }
    isStopping = false;
}
```

The function first tells the thread to interrupt itself and its child threads using `Interrupt()` after setting up an internal flag. Then, the function waits for the thread and its child threads to stop for 60 seconds (60,000 milliseconds). After all threads get stopped, the `isReady` flag gets set to `false`, which means that the kernel thread can't be started again until regeneration is complete. As `Stop()` regenerates the kernel thread by default, the flag gets set to `true` almost instantly, which means that the same thread can start again.

This is a foundation to the solution to the kernel thread regeneration problem, and the code for `Regen()` is as below (debugging code is excluded):

```csharp
public void Regen()
{
    // We can't regen the kernel thread unless Stop() is called first.
    if (IsReady && BaseThread.ThreadState == ThreadState.Running)
        throw new KernelException(KernelExceptionType.ThreadOperation, LanguageTools.GetLocalized("NKS_KERNEL_THREADING_EXCEPTION_REGENRUNNING"));

    // Remake the thread to avoid illegal state exceptions
    if (IsParameterized && ThreadDelegateParameterized is not null)
        BaseThread = new Thread(ThreadDelegateParameterized) { Name = Name, IsBackground = IsBackground };
    else if (ThreadDelegate is not null)
        BaseThread = new Thread(ThreadDelegate) { Name = Name, IsBackground = IsBackground };
    else
        throw new KernelException(KernelExceptionType.ThreadOperation, LanguageTools.GetLocalized("NKS_KERNEL_THREADING_EXCEPTION_CANNOTREGEN") + $". {Name}");
    isReady = true;
}
```

The above call to the constructor solves the consistency problem that may be prominent in large codebases to ensure that all generated threads are created in exactly the same way, with the thread name (for easier debugging), the background state, and the thread delegate. Moreover, the above function, once the base thread gets successfully regenerated, the `isReady` flag gets set to `true`, if the kernel thread has stopped.

## Maintaining the list of threads

Nitrocid currently maintains the list of kernel threads that got created during the lifetime of the application under an internal field called `kernelThreads` in the `ThreadManager` class, because the constructor automatically adds the kernel thread to this list. The constructor of the `KernelThread` adds the kernel thread to this list (debugging code is excluded):

```csharp
private KernelThread(string ThreadName, bool Background, ThreadStart Executor, bool Child, KernelThread? ParentThread)
{
    InitialThreadDelegate = Executor;
    Executor = () => StartInternalNormal(InitialThreadDelegate);
    BaseThread = new Thread(Executor) { Name = ThreadName, IsBackground = Background };
    IsParameterized = false;
    ThreadDelegate = Executor;
    Name = ThreadName;
    IsBackground = Background;
    isReady = true;
    if (Child && ParentThread is null)
        Child = false;
    if (!Child)
        ThreadManager.kernelThreads.Add(this);
    else
        parentThread = ParentThread;
}
```

This allows `ThreadManager.KernelThreads` to give you a list of kernel threads as below:

```csharp
public static List<KernelThread> KernelThreads =>
    kernelThreads;
```

As a result, stopping all kernel threads when Nitrocid shuts down with `StopAllThreads()` is possible, because it traverses through the above list and calls `Stop()` on each one of them with regeneration enabled.

## Can I try it out on other apps?

Currently, this flexibility is only available on Nitrocid's base library, but we are planning on expanding the availability to a wider range of applications under a new, separate library, which will be released in the second half of this quarter.
