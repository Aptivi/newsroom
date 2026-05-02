+++
date = '2026-05-02T15:01:57+03:00'
title = 'Threadify is now available!'
+++

Earlier, we have made an article on Aptivi Newsroom that described the process of creating threads in Nitrocid, as you can see [here](/newsroom/other/0001-how-nitrocid-manages-threads), where we had introduced a custom thread class that stores the actual thread class and manages it.

As a result, applications can now restart threads in a single call to a function, which abstracts the work of having to maintain all the thread properties, such as name and action, yourself when re-creating a new instance of the thread class.

When Nitrocid introduced the thread management feature for the first time, it was made as a solution to a problem that plagued `System.Threading.Thread` when it comes to [`Interrupt()`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.interrupt?view=net-10.0#system-threading-thread-interrupt) and then starting the thread again. When the thread is finally interrupted or terminated either automatically or by `Interrupt()`, the thread state, which [`ThreadState`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.threadstate?view=net-10.0) manages, goes to `Stopped`, which means that [`Start()`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.start?view=net-10.0#remarks) won't work again.

This flexibility used to be exclusive to Nitrocid and its API for kernel modifications to take advantage of thread restarting and other threading features. Now, it's no longer the case as we're announcing a brand new project that brings the same flexibility but under a different library!

## Threadify v1.0

We are very excited to announce that the first version of Threadify is now available to project developers for C# applications! This library brings the same flexibility that Nitrocid presented when the feature was first introduced to the kernel, and stability was proven.

Currently, this is a port of kernel threading code to both achieve the following goals:

* Provides an easy way for developers to manage threads more easily.
* Provides an ability to restart threads with a single line of code.
* Provides thread management tools that allows listing threads and testing the actual timing of [`Thread.Sleep()`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.thread.sleep?view=net-10.0).

Let us give you a quick rundown on how a Threadify thread starts. When you create a thread class, called `ThreadInstance`, the thread that this class manages gets created with the provided constructor parameters, which are:

* **Thread name**: Name of the thread that this class stores for each thread class (re)generation
* **Background**: Whether this thread is part of the background or the foreground
* **Executor**: Either a single function or a function with one object that contains thread parameters

The constructor makes a new `Thread` class, sets up nested thread parameters (if any), and marks the `ThreadInstance` as ready, evidenced by `isReady` being true. You can verify the readiness of the thread by checking `IsReady`.

When `Start()` is called, the thread starts under the following conditions:

* If the thread is ready to start (that is, `IsReady` is `true`). An exception will be thrown if otherwise.
* If the thread state is not `ThreadState.Stopped`. The thread doesn't start if otherwise.
* If the thread is not already running (that is, `IsAlive` is `false`). The thread doesn't start if otherwise.

Future versions of Threadify will provide more features during the lifetime of the project, and we will make an announcement if such updates happen.

> Please note that the documentation is currently not available yet, but we are working on it soon.

## Installing Threadify

To install Threadify, read the manual as linked [here](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade).