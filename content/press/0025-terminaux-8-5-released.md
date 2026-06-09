+++
date = '2026-06-09T20:52:11+03:00'
title = 'Terminaux 8.5 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the fifth point release for Terminaux v8.x series today!

This version of Terminaux is fairly small, but it introduces support for new color models (YPbPr, YDbDr, and LMS) that were introduced with an update to Colorimetry v1.1, as well as a color wheel that was introduced to the color selector TUI.

## New features

This version of Terminaux adds new features that will make your interactive textual user interface applications written in C# more powerful, including, but not limited to:

* **Added new color models support**: With an update to Colorimetry v1.1, we have introduced new color models we've mentioned above earlier. Terminaux is now able to process colors that were created with one of the three color models as a specifier
* **Added color wheel to the color selector**: The color wheel has been added to the color selector TUI. It shows you a full screen color wheel that contains a white blip pointing to the current color.
* **Added cancellable input infobox**: Input infoboxes can be cancelled by pressing ESC on your keyboard. Terminaux had no way to allow you to press ESC on an input infobox, but this version now lets you do it.

Below shows you more details about the new features that we have highlighted as the biggest part of this version of Terminaux.

### New color models

Terminaux applications can now process color instances that were made with the specifiers that are one of the following:

* YPbPr: Made with `ypbprsdtv:<yyy>;<pb>;<pr>`, `ypbprhdtv:<yyy>;<pb>;<pr>`, or `ypbprhivi:<yyy>;<pb>;<pr>`
* YDbDr: Made with `ydbdr:<yyy>;<db>;<dr>`
* LMS: Made with `lms:<lll>;<mmm>;<sss>`

Colorimetry v1.1 was actually responsible for adding those color models to the codebase, but Terminaux adopted those changes from the update since we decoupled the color code from this library into Colorimetry that was publicly released early this year. Both Terminaux and non-Terminaux applications can now benefit from added color models.

To give you a brief explanation, YPbPr is an analog video signal carried by component video cable, which consists of a green cable (Y), a blue cable (Pb), and a red cable (Pr), and is found on old televisions and other analog system equipment. YCbCr is intended for digital video, but we haven't included this color model yet. YDbDr is the standard for SECAM analog color television broadcasting standard, where luminance is Y, scaled result of subtraction of Y from blue signal is Db, and scaled result of subtraction of Y from red signal is Dr.

On the other hand, the LMS is a color space which represents the response of the three types of cone cells in a human eye, named according to their responsivity. It's used when performing chromatic adaptation, as well as studying color blindness.

### Added color wheel to the color selector

![Showcase](https://aptivi.gitbook.io/aptivi/~gitbook/image?url=https%3A%2F%2F1870312457-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FG0KrE9Uk2AiblqjWtpAo%252Fuploads%252Fg85SBP6PnqarxNCaj50s%252Fimage.png%3Falt%3Dmedia%26token%3D73622314-17d8-485b-9c6f-0ed6552588b1&width=768&dpr=3&quality=100&sign=1a238ad5&sv=2)

You can now access the actual color wheel from the interactive color selection textual user interface (TUI) that allows you to take a look at a visual representation of a selected color under a circle of rainbow colors, which covers the whole range of colors according to the hue value (all angles from 0° to 360°). A white blip that is placed on a gray bezel points to a selected color hue. For example, if you've selected Blue, a white blip will move to the appropriate location, which points to the blue color according to the hue value.

The color wheel also supports lighting and saturation, which changes the brightness and contrast of the color wheel according to the chosen color and its properties. For example, if you have chosen a gray color, the whole color wheel would turn gray, and the white blip will usually point to the default angle, which points to the red color.

### Added cancellable input infobox

Previously, Terminaux didn't allow you to easily cancel the input infobox quickly by pressing the ESC key. Since we wanted the behavior of this input informational box to align with the rest of the modal infoboxes, we've decided to implement this change, as part of our plan to implement a more powerful keybinding handling system for the terminal reader.

Starting from Terminaux 8.5, applications can now let you press ESC in an input infobox to imply that the user has cancelled the input.

## Improvements

We are always working on improving Terminaux in between updates to ensure that Terminaux-powered applications become more reliable than before.

## Upgrading Terminaux

To upgrade Terminaux to v8.5, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
