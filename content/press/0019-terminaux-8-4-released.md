+++
date = '2026-05-17T13:23:41+03:00'
title = 'Terminaux 8.4 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the fourth point release for Terminaux v8.x series today!

This version of Terminaux utilizes SpecProbe v3.9.0 and BassBoom v1.0.0, which bring complete support for FreeBSD. This aligns with our plan to provide official support for FreeBSD systems, and this support came to fruition with the release of both [SpecProbe v3.8.1](/newsroom/press/0007-specprobe-3-8-1-released-with-initial-freebsd-support), while required improvements for FreeBSD support were integrated with the release of version v3.9.0.

## New features

This version of Terminaux adds new features that will make your interactive textual user interface applications written in C# more powerful, including, but not limited to:

* **Added FreeBSD support**: Full FreeBSD support has been finally added with the introduction of SpecProbe v3.9.0 and BassBoom v1.0.0, which allow you to run Terminaux-powered applications on FreeBSD systems.
* **Added cowsay renderer**: ASCII characters that talk or think have now been added to Terminaux, commonly known as Cowsay. This uses a simple cyclic writer class to render a cow or a character speaking or thinking about something.
* **Added timed input**: You can now listen for input, whether it's a mouse or a keyboard, until a specified timeout has been reached. If a user didn't press a key or move a mouse within the specified timeframe, the application handles the timeout.

Below shows you more details about the new features that we have highlighted as the biggest part of this version of Terminaux.

### FreeBSD support

Terminaux applications can now fully run within FreeBSD systems. This means that you can now use Terminaux-powered applications on FreeBSD systems without any issues. This is one of our plans to provide official support for FreeBSD system, which happened with the release of SpecProbe v3.8.1 and v3.9.0, which complemented each other in regards to supporting FreeBSD systems.

Since April 2026, we have been working hard to ensure that FreeBSD systems are supported with our projects. Nitrocid v0.2.1 and newer versions of Nitrocid v0.2.0 and v0.1.0 will be able to fully run on FreeBSD systems without any issues. We will release the backported versions by the end of this week, if everything's green.

### Added cowsay renderer

![Showcase](https://sites.gitbook.com/preview/site_LNykF/~gitbook/image?url=https%3A%2F%2F1870312457-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FG0KrE9Uk2AiblqjWtpAo%252Fuploads%252F97xHhbFT1o2AUFjEqLOl%252Fimage.png%3Falt%3Dmedia%26token%3Df56a470a-1f46-449a-a6e9-22910bb92231&width=400&dpr=3&quality=100&sign=740087a2&sv=2)

The cowsay renderer has been added to Terminaux as part of the simple cyclic writers group. It allows your console application to print out an ASCII art that shows a character, such as a cow or other object, speaking or thinking about something. This renderer is easy to use, and supports alignment in the aligned version of the writer, as well as color support.

To get started with using the renderer, Just create an instance of the renderer using the following snippet:

```csharp
var cowsay = new CowsayText(CowName.Default, "Hello world!");
TextWriterRaw.WriteRaw(cowsay.Render());
```

In case you want alignment, you can use the aligned version of the renderer:

```csharp
var cowsay = new AlignedCowsayText(CowName.Default, "Hello world!")
{
    Settings = new()
    {
        Alignment = TextAlignment.Middle
    }
};
TextWriterRaw.WriteRaw(cowsay.Render());
```

### Added timed input

One last addition for this monthly release of Terminaux is the timed keyboard and mouse input, where Terminaux waits for an input in a specified amount of milliseconds before it reports a timeout. Using a new function, `ReadPointerOrKeyUntil()`, that is introduced in this version, you can extract the two values that describe the status of the read:

* `result`: It either contains input event data or a null event data.
* `provided`: True if input has been provided before the timeout occured; otherwise, false.

You can get started with using the timed input with this minimal code:

```csharp
(InputEventInfo result, bool provided) = Input.ReadPointerOrKeyUntil(new(0, 0, 5));
```

## Improvements

In addition to new features, we have also integrated some of the most important improvements, including fixes to figlet selector and general improvements regarding text wrapping. It also utilizes Threadify for shell-related operations, as well as various improvements.

## Upgrading Terminaux

To upgrade Terminaux to v8.4, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).