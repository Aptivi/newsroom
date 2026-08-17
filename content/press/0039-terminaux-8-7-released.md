+++
date = '2026-08-17T22:44:30+03:00'
title = 'Terminaux 8.7 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the seventh point release for Terminaux v8.x series today!

This version of Terminaux brings a minimal amount of new features, but brings a host of improvements made to the Terminaux shell and its command management interface.

## New features

This version of Terminaux adds new features that will make your interactive textual user interface applications written in C# more powerful, including, but not limited to:

* **Added further theme customization**: We have added further customization to the theme instance, allowing seamless edits.
* **Added color conversion commands**: We have ported the color conversion commands from Nitrocid to Terminaux.

Below shows you more details about the new features that we have highlighted as the biggest part of this version of Terminaux.

### Theme customization

We have added more customization options to the theme instance so that you can edit the theme metadata, such as event-related settings, name, and description. Previously, if you wanted to edit such properties, you had to create an empty theme metadata representation and call the constructor manually, then add all the colors. Now, you no longer have to do this, because we have finally made those properties editable.

You can now edit theme properties like this (example taken from [here](https://github.com/Aptivi/Nitrocid/blob/main/public/Nitrocid.Addons/Nitrocid.Extras.ThemeStudio/Studio/ThemeStudioCli.cs#L198)):

```csharp
var ThemeInfo = new ThemeInfo()
{
    Name = theme,
};
foreach (var originalColor in originalColors.Keys)
    ThemeInfo.SetColor(originalColor, originalColors[originalColor]);
```

### Color conversion commands

Nitrocid used to provide you with commands that allow you to convert between color models in various formats. They were not in sync with the latest changes made to Colorimetry, so we have moved them to Terminaux to make those commands accessible to all shells. You can now access the following commands:

* `colorto`
* `colortoks`
* `colortohex`
* `colorspecto`
* `colorspectoks`
* `colorspectohex`

We have also added support for all color models that Colorimetry supported in the newest version, such as YCbCr, YPbPr, and YDbDr.

## Improvements

This version of Terminaux contains many improvements that make your console applications stronger and more reliable, such as:

* **Command class structure improved**: We have improved the command class structure so that you can directly implement command information properties within the command classes themselves as overridable properties instead of adding another entry of command info class (which we've removed) to the long list of such classes that will be filled with constructors that can get quite long. As a result, you can now more efficiently implement commands without any friction.

We are always working on improving Terminaux in between updates to ensure that Terminaux-powered applications become more reliable than before.

## Upgrading Terminaux

To upgrade Terminaux to v8.7, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
