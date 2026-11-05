+++
date = '2026-11-05T13:40:13+03:00'
title = 'Terminaux 8.9 Released'
+++

Since the release of Terminaux v8.0 on October 13th, 2025, more than six months came and went with continuous bug fix and feature releases, which brought improvements to all the console applications that are written in C#. This version was a long-term support release that added many interesting features while improving the performance of all console applications in all platforms, including Windows, macOS, and Linux.

In an effort to keep providing a minimal set of feature additions while adding bug fixes and general improvements, we are very thrilled to release the ninth point release for Terminaux v8.x series today!

This version of Terminaux is a small release that adds a new way to make combo box modules while incorporating several improvements. This is also the first version of Terminaux released within the second year of long-term support since the release of v8.0.

## Easier building of combo box modules

When you were building combo box modules for multi-input info boxes or any other input method that utilize input modules, such as presentations, you may have noticed that building combo box input module instances may have been difficult. That's because you had to construct an array of choice categories for a property where choices are defined.

As a result, if you wanted to populate a list of choices without categories or groups, you had to define an array of choice categories that has only one category instance, which - in turn - takes an array of groups that has only one group instance, which - in turn - takes an array of actual choices you want to define. This can be tedious at times.

Starting from Terminaux 8.9, we've added new constructors that make it easier for you. Instead of manually providing an array of choice categories, you have three choices to use this constructor:

  * Using `InputChoiceCategoryInfo[]`: You can use a constructor that takes an array of choice categories.
  * Using `InputChoiceGroupInfo[]`: You can use a constructor that takes an array of choice groups.
  * Using `InputChoiceInfo[]`: You can use a constructor that takes an array of choices.

This doesn't only apply to normal combo box modules, but also applies to multiple choices input module. You can now define your input modules like this:

```cs
InputChoiceCategoryInfo[] moduleCategories =
    [
        new("Selection infobox", [new("Available options",
        [
            new("Acid House", ""),
            new("Big Room", ""),
            new("Deep House", ""),
            new("Drum-n-Bass", ""),
            new("House", ""),
            new("Techno", ""),
            new("Trance", ""),
        ])])
    ];
InputChoiceGroupInfo[] moduleGroups =
    [
        new("Available options",
        [
            new("Windows", ""),
            new("macOS", ""),
            new("Linux", ""),
        ])
    ];
InputChoiceInfo[] moduleChoices =
    [
        new("Green", ""),
        new("Blue", ""),
        new("Red", ""),
        new("Fuchsia", ""),
        new("Aqua", ""),
        new("Orange", ""),
        new("Black", ""),
        new("White", ""),
    ];

var modules = new InputModule[]
{
    new ComboBoxModule(moduleCategories)
    {
        Name = "EDM Music Genre",
        Description = "Choose one of the EDM music genres to continue",
        Value = 6,
    },
    new ComboBoxModule(moduleGroups)
    {
        Name = "Preferred Operating System",
        Description = "Choose your preferred operating system to continue",
    },
    new MultiComboBoxModule(moduleChoices)
    {
        Name = "Favorite Colors",
        Description = "Choose your favorite colors",
    },
};
```

## Tidier selection choices

Selection choices used to push the available choices by two cells, regardless of whether the group array in different categories contains only one group or not. As a result, in some cases, the selection choices in the choice selection screen might appear a bit inconsistent, especially when the group name doesn't show up for a single category.

We've improved the behavior so that selection choices appear consistently, giving you a cleaner look. Now, whenever selection choices are rendered, Terminaux determines whether the choices get pushed by two cells or not using the following method:

  * Iterates through different categories to get the list of groups
  * Checks to see if a group array contains more than one group
  * Tells Terminaux to push the selection choices two cells forward

A more uniform look is then achieved, ensuring consistency in rendering the available selection choices in the selection textual user interface.

## Improved tab handling

Tab handling in Terminaux used to simply replace all instances of tab characters with four spaces, depending on the configured tab width. However, this could cause the layout to look messy, especially when it comes to rendering text containing lots of tab characters for values, such as manual tab-separated tables.

We've improved how Terminaux handles tabs so that it takes such situations into account to maintain a consistent layout when it comes to rendering text that contain those characters for aesthetic purposes. From now on, Terminaux does the following:

  * Iterates through the character set in the string
  * If the character is a tab, it takes a fragment of the string until the tab index
  * It estimates the width of the text in cells
  * It calculates how many spaces are needed to meet the tab width
  * It replaces the tab character with the required amount of spaces

Once this is done, text that requires tabs to render exactly as it appeared in text editors should be rendered properly. That's because we've changed how the plain text writers worked; they automatically replaces tabs with spaces if needed.

## Improvements

This version of Terminaux contains many improvements that make your console applications stronger and more reliable. We are always working on improving Terminaux in between updates to ensure that Terminaux-powered applications become more reliable than before.

## Upgrading Terminaux

To upgrade Terminaux to v8.9, follow the instructions by [reading the manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
