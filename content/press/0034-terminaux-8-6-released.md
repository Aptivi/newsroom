+++
date = '2026-07-16T12:56:57+03:00'
title = 'Terminaux 8.6 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the sixth point release for Terminaux v8.x series today!

This version of Terminaux is a rather big release that brings in new, exciting features, as well as improvements made to several parts of Terminaux in both the functional and the developmental level.

## New features

This version of Terminaux adds new features that will make your interactive textual user interface applications written in C# more powerful, including, but not limited to:

* **Added Prosery and Quote writers**: We have added two writers that allow you to render both prosery and quotes in an awesome formatting. With the usage of simple writers, you can print them in both the CLI and the TUI applications.
* **Added high-density canvas**: High-density canvases now allow you to render pixel art in higher resolution. This means that you have more pixels to craft a beautiful art and display it to your console while using less space.
* **Added horizontal scrolling support for mouse**: With an enhanced input system that Terminaux provides, we have finally added horizontal wheel scrolling support for mouse events. This means that your Terminaux applications can now react to users using the horizontal scrolling wheel on the mouse to scroll left and right.
* **Added input locks**: With input locks, you can now make Terminaux wait until the lock has been released by another thread or routine in your application.

Below shows you more details about the new features that we have highlighted as the biggest part of this version of Terminaux.

### Prosery and Quote writers

![Showcase](https://aptivi.gitbook.io/aptivi/~gitbook/image?url=https%3A%2F%2F1870312457-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FG0KrE9Uk2AiblqjWtpAo%252Fuploads%252FsI7hSiaaKa1xlMi0WKPH%252Fimage.png%3Falt%3Dmedia%26token%3D145f7458-2338-4490-bf8d-723ab57b13f6&width=400&dpr=3&quality=100&sign=9d19842&sv=2)

Terminaux applications can now render prosery and other text to an awesome layout with a left padding using a dedicated writer. This writer, called `Prosery`, allows you to print lines of text, such as prosery or poetry, with an optional line wrapping function and color customization. This is great for console applications that show you literary text, whether it's a command-line interface or a textual user interface.

Line wrapping function can also make your prosery more readable by taking the text width into account when wrapping it. You can customize the text width, or you can manually wrap the lines yourself by adding new lines to portions of text, such as poetries that have specific syllable count in each line.

![Showcase](https://aptivi.gitbook.io/aptivi/~gitbook/image?url=https%3A%2F%2F1870312457-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FG0KrE9Uk2AiblqjWtpAo%252Fuploads%252FcSSsLmwJjtmBgh6I8IpO%252Fimage.png%3Falt%3Dmedia%26token%3De388ccf1-98bc-4dc4-8ee2-c9c36edbdae9&width=400&dpr=3&quality=100&sign=cf9884e7&sv=2)

Another cyclic writer is derived from the `Prosery` writer, called `Quote`, appears in Terminaux, which allows you to write a sentence or paragraph with attribution at the bottom of the text. This derivation lets you have the same level of configuration that the prosery writer gives you, but quotes render with italic text.

Both writers are simple cyclic writers, which means that they can be used with all kinds of applications, such as CLI and TUI apps.

### High-density canvases and simple canvases

![Showcase](https://aptivi.gitbook.io/aptivi/~gitbook/image?url=https%3A%2F%2F1870312457-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FG0KrE9Uk2AiblqjWtpAo%252Fuploads%252FgKeEgNeWGnRloLcIMIrl%252Fimage.png%3Falt%3Dmedia%26token%3D465a8b76-7c0b-485b-9ef5-8873900df04a&width=400&dpr=3&quality=100&sign=5293d2e2&sv=2)

Based on the recent addition of QR code renderer, which used high-density pixel rendition to draw a QR code to the console while taking up less space in your console, we've added simple canvases that can be rendered without specifying the position. This way, those canvases are usable in both the CLI and the TUI apps, and they can be accessible via the `SimpleCanvas` writer. This writer has the same feature parity with the graphical `Canvas` writer, which means that you can easily migrate between graphical and simple canvas writers with little effort.

However, we understand that some pixel art can't be rendered on consoles with default resolution and density without taking up lots of space, such as large pixel arts with details that can only be expressed in large canvases, so we've decided to implement a new property that lets you render your art in high density. This means that pixel art can now be rendered in higher resolution without taking up lots of space.

You can turn this on in your canvas by turning on the `HighDensity` property. For the best experience, make sure that `DoubleWidth` is off. We will make it easier for you in a future Terminaux update.

### Horizontal scrolling support for mouse

Previously, Terminaux didn't allow you to create console applications that rely on horizontal scrolling, as we didn't implement support for such mouse events. Horizontal scrolling can only be found in some mice, such as some Logitech mice (MX Master 3s, MX Master 4, and so on), and laptop touchpads that support this scrolling direction. Users can use this wheel to scroll through content horizontally, such as from left to right or from right to left, and is usually accessible using your thumb.

Starting from Terminaux 8.6, the input system now supports horizontal scrolling, which means that Terminaux applications can now react to horizontal scrolling in the same way they react to vertical scrolling. Not only that, it's also available in all platforms, including Windows, macOS, Linux, and FreeBSD!

### Input locks

Terminaux also implements input locks so that your application can wait until the lock condition evaluates to `true`. For example, on applications with screensaver and other features that require input locks like Nitrocid, you can use this feature so that inputs don't conflict with each other. By default, locks are enabled with an unconditional unlock, but you can edit either the default lock or the session-specific lock, or disable locks per session, so that you can satisfy different needs.

Global input locks can be utilized by setting the following properties:

* `DefaultLockCondition`: The function that is used when there is no session-specific lock evaluation function is being specified. This function will have to eventually evaluate to `true` at some point, such as when one tries to exit the screensaver.

Additionally, you can use function overloads with the following parameters to control the locking behavior:

* `lockCondition`: Specifies the lock condition that will be used instead of the global lock condition. It often has higher priority than the global lock condition evaluation function.
* `disableLock`: Specifies whether to force Terminaux to return user input even if the lock condition evaluates to false or not.

## Improvements

This version of Terminaux contains many improvements that make your console applications stronger and more reliable, such as:

* **Improved grapheme cluster support**: Recent changes to the cell width estimation have been made to better handle grapheme clusters across different areas of Terminaux. Instead of relying solely on surrogate pairs, we are now relying on grapheme clusters for different characters that can't be expressed using simple surrogate pair sequences, such as emojis with modifiers, emojis with zero width joiners, and other complex emoji sequences. This allows Terminaux to better handle situations where such sequences are either entered as user input or printed as console output, increasing reliability.
* **Several graphical writers moved to simple writers**: We've made several breaking changes that allow several graphical writers that could have been implemented as simple writers to become one. As a result, several writers of this type, such as tables; calendars; syntax text; text path; single-value showcases; and double-value showcases, have been converted to simple writers so that non-graphical Terminaux applications can use them without having to rely on positioning.

We are always working on improving Terminaux in between updates to ensure that Terminaux-powered applications become more reliable than before.

## Upgrading Terminaux

To upgrade Terminaux to v8.6, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
