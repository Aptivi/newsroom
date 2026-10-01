+++
date = '2026-10-01T11:42:14+03:00'
title = 'Terminaux 8.8 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the eighth point release for Terminaux v8.x series today!

This version of Terminaux brings promising features while bringing back some of those that were removed in earlier versions of Terminaux, including the table-based choice renderer.

## Cancellation of inputs

Before this release, applications had to make some wild guesses as to whether the input was cancelled or not when dealing with empty input. A user decides to cancel the input by just pressing `ENTER`, but the application had no way of distinguishing between the input submission, which ENTER currently does, and the input cancellation, which is something a user may try to do.

As a result, the application may behave as if empty user input has been accepted, even if the user has no intention on submitting it. Therefore, searches would run, connections to empty host name would start, and so on, even if the user didn't expect the application to go on.

To solve this problem, we've decided to add an extra property to the input reader state, called `Cancelled`, that lets any keybinding specify whether the input would be cancelled once it completes or not. You can try that out by pressing ESC on your keyboard during input, and watch as the application becomes aware that the user intends to cancel the input, thus the operation won't continue.

Additionally, input informational boxes are now aware of the input cancellation scenario where a user might press `ESC` to cancel input in informational boxes, so we've added an extra argument to the input infobox function, called `out bool done`, that lets graphical apps specify whether the input was processed or not. This way, if a user requests cancellation using ESC, this variable would turn to false, and apps use this value to determine whether cancellation is requested.

You can check the cancellation state from the input reader settings instance like this (after `Read()` is called):

```csharp
done = !(readerSettings.state?.Cancelled ?? false);
```

Input infoboxes abstract this from you using the `done` output argument, meanint:

  * `true`: if input was submitted (for example, `ENTER` was pressed)
  * `false`: if input was cancelled or an error occurred (for example, `ESC` or `CTRL + C` was pressed)

## New search modes

When we implemented choice search for the first time, it was presented as a solution to searching through hundreds or thousands of choices, such as a list of countries or all cities around the world. We implemented it as a case-insensitive search mode, but we wanted to provide regular expression based search for more efficiency.

Unfortunately, we had replaced the former search mode with the regular expression mode, which caused us to change the search behavior with no way to go back to the older search mode, with a plan to implement it again.

Terminaux 8.8 now provides you a way to use the older case-insensitive search mode, along with the regular expression based search mode, by pressing the `F` key or the `SHIFT + F` key on choice infoboxes, selection prompts, and interactive selector TUIs, respectively.

So, you have two keybindings for different search modes:

  * `F`: Case-insensitive search mode
  * `SHIFT + F`: Regular expression search mode

## Table choice styles

Before Terminaux 5.0 was released back on August 26th, 2024, the table renderer was one of the choice styles that uses the table renderer code to show you a comprehensive table of choices. The table, back then, used a simple way of rendering the table, but we had refactored it to support both positioning and sizing, which led to the removal of the table choice style as the choice style was meant to be used in the command-line interface, not the textual UI.

Since then, we worked on simple and graphical cyclic writers, starting from 6.0, which got a massive overhaul since the release of 7.0. Afterwards, we poured a lot of hard work in refactoring those writers to simplify some of the graphical writers by stripping positioning-related code. The table renderer was one of them, which caused it to be suitable again.

Since then, the table choice style has been brought back with this version of Terminaux, which uses the simple table renderer.

## Improvements

This version of Terminaux contains many improvements that make your console applications stronger and more reliable, such as:

  * **Improved keybinding handling**: In interactive TUIs, keybinding handling has been improved to bring back custom keybindings to the main keybindings informational box. Instead of opening a separate help page for extra keybindings, which is more time consuming, you can now simply press `K` to get a complete list of keybindings. This uses a list of keybindings that are added to the textual TUI abstract class, called `HelpAdditionalBindings`.

We are always working on improving Terminaux in between updates to ensure that Terminaux-powered applications become more reliable than before.

## Upgrading Terminaux

To upgrade Terminaux to v8.8, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
