+++
date = '2026-11-15T19:53:41+03:00'
title = 'Terminaux 8.10 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the tenth point release for Terminaux v8.x series today!

This version of Terminaux is just another small release that adds a new way to make combo box modules while incorporating several improvements. This is also the first version of Terminaux released within the second year of long-term support since the release of v8.0.

## Tidier list of commands

When you were using the `help` command without arguments to get a list of available commands, you might have noticed that some of the commands get rendered longer than the console window width due to a long list of usages, especially the color conversion commands. As a result, it might have made it harder for users to navigate through a list of commands effortlessly.

To reduce noise, we've decided to move the usage outside the command list, and make it available only for those who request more information about a command using the `help <command>` command syntax. Now, whenever you request a list of commands, you'll only get their names and their descriptions, which makes the list cleaner than before.

If you request more information about a command, you'll see something similar to this:

```
Command: colorto
Description: Converts the source color model to the target color model in numbers.

Usage: colorto [-set=value] sourceModelName targetModelName <number1:int> <number2:int> <number3:int> [number4:int] [number5:int]

This command has the below arguments that change how it works:
  sourceModelName: Source color model
    rgb/ryb/cmy/cmyk/hsv/hsl/yiq/yuv/xyz/yxy/cielab/cielch/cieluv/hwb/hunterlab/lms/ycbcrsdtv/ycbcrhdtv/ycbcrhivi/ypbprsdtv/ypbprhdtv/ypbprhivi/ydbdr
  targetModelName: Target color model
    rgb/ryb/cmy/cmyk/hsv/hsl/yiq/yuv/xyz/yxy/cielab/cielch/cieluv/hwb/hunterlab/lms/ycbcrsdtv/ycbcrhdtv/ycbcrhivi/ypbprsdtv/ypbprhdtv/ypbprhivi/ydbdr
  number1: First number
  number2: Second number
  number3: Third number
  number4: Fourth number
  number5: Fifth number

This command has the below switches that change how it works:
  -set: Sets the value of the output to the selected MESH variable
```

## Improved appearance of exception renderer

Due to the introduction of localization back in 2025, the exception renderer still rendered text in English, which caused inconsistencies when displaying text that may have been in another language. The exception renderer allows you to render a list of both inner and outer exceptions with color-coded components to make it easier to read.

Now, we've improved the appearance of the exception renderer by utilizing colors and by using language-agnostic by replacing text with symbols and arrows. This way, the exception renderer would look more polished.

```
InvalidOperationException: Failed to handle exception. Huh?
  -> TestExceptionInner.RunFixture() [0x0000001B] @ C:\Users\aptiv\Aptivi\Source\Public\Terminaux\private\Terminaux.Console\Fixtures\Cases\Writer\TestExceptionInner.cs:43,21
    Exception: This can't happen.
      -> TestExceptionInner.RunFixture() [0x0000000C] @ C:\Users\aptiv\Aptivi\Source\Public\Terminaux\private\Terminaux.Console\Fixtures\Cases\Writer\TestExceptionInner.cs:36,17
```

## Show which arguments are unsatisfied

When it comes to running commands that have several argument requirements, such as exact wording, numeric arguments, or required arguments, if the user didn't provide the required arguments correctly, they'll see error messages telling them that there were some arguments that were unsatisfied. Unfortunately, the user may not know which error caused the command not to execute, apart from the message, without helpful information that may help them pinpoint the issue.

We've improved the parser mechanism by adding a list of arguments and/or values that may help them pinpoint the issue so that they can correct the command syntax quickly. We're now not only listing which errors needs to be corrected, but we're also listing the arguments and/or their values that caused the parser to fail.

```
[-6] > colorto rgb reb 1 2
Required arguments are not provided for all usages below:
- [1] colorto [-set=value] sourceModelName targetModelName <number1:int> <number2:int> <number3:int> [number4:int] [number5:int]
Required arguments are not provided.
- 1: number3

One or more of the arguments expect an exact wording, but you provided an invalid word.
- 1: targetModelName / reb

Consult the help entry for this command for more info
```

## Improvements

This version of Terminaux contains many improvements that make your console applications stronger and more reliable. We are always working on improving Terminaux in between updates to ensure that Terminaux-powered applications become more reliable than before.

## Upgrading Terminaux

To upgrade Terminaux to v8.10, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
