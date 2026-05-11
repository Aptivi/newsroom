+++
date = '2026-05-11T17:28:16+03:00'
title = 'VisualCard Enters Maintenance Mode'
+++

The first version of VisualCard, which was v0.1.0, was released on February 20th, 2023, to provide suppot for thr most basic features of the vCard specifications v2.1, v3.0, and v4.0. Since then, we've expanded the library to add new features and new enhancements to make this vCard parser smoother and more reliable than before during four years of new versions.

VisualCard has become more than 3 years old, and there was a new major version, v4.0.0, which was released on February 2025. Since then, only minor updates were being done as we were evaluating whether we continue to add new features or to mark this project as feature-complete.

VisualCard v1.0 was released to give VisualCard a complete overhaul when it comes to parsing contacts. This makes sure that more vCards can be parsed, and that global line folding works everywhere. The second major version, v2.0, was released for nested cards and UIDs, while v3.0 was released to add more features to the point that we've implemented almost the entire set of RFCs for cards.

The fourth major version (and the last one), v4.0, was released to add support for editable cards by adding, editing, and deleting properties.

After reviewing the source code and the library's functionality, we've decided to mark this project as feature-complete. This means that the following will happen:

* VisualCard has entered maintenance mode, which means that there will no longer be new features unless a bug fix requires adding a new feature.
* Breaking changes in the VisualCard API itself won't be accepted in any future release.
* The extra features will continue to be added, as long as they don't affect the base library or its functionality, until December 31st, 2026.
* New versions will be released in a much slower pace than usual, and those versions will introduce bug fixes and general improvements.

If you are using VisualCard or reporting feedback to us during the feature addition phase, thank you so much! This library was made because we wanted to provide an easy and RFC-compliant vCard parser for C# applications that run over .NET Framework and the modern .NET framework.
