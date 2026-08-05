+++
date = '2026-08-05T10:38:45+03:00'
title = 'Terminaux 6.1 and 7.0 are now unsupported'
+++

Terminaux 6.1 was released on top of 6.0 to add more new features, and they were released on December 22nd, 2024, and January 13th, 2025, respectively. Originally, the version series was supposed to be released later, but unexpected events during development with an unpredictable aftermath not only caused us to release the version earlier than expected, but also caused us to release two minor versions to fix some last-minute bugs.

Terminaux 6.0 added many new features to different parts of the library, such as audio cues, color tools, cyclic writers and screens, aligned text writers, beep synths, command-line argument parsing, shells, and more. Later, version 6.1 expanded on this area by adding features like full-screen editors and writers, wrapped writers, and modern argument parser, with some features that arrived in both versions coming from Nitrocid.

Meanwhile, version 7.0 was released on August 10th, 2025, to add some more features, such as the expanded shell features taken straight from Nitrocid, as well as theme management, categorized cyclic writer rendering, and more infobox variants. Also, we've added multi-input infoboxes, padding and margins, Asciinema, and much more.

The release of version 8.x series was being worked on afterwards, with many new features being added since the October 13th, 2025, release, such as support for hidden commands, global password mask, and markdown export. It was considered a long-term support release, with monthly releases being done.

Terminaux 6.1.x and 7.0.x were scheduled to end their support as of August 5th, 2026, after careful consideration.

Starting today, both 6.1.x and 7.0.x will no longer receive any official support. This means that:

  * No security updates will be made.
  * No general updates will be made, alongside the security ones.
  * No official support will be provided to those who continue to use them in their projects.

We recommend that you upgrade your projects to utilize Terminaux 8.x, with the latest version at the moment being 8.6.1, to continue receiving official support with more bug fixes and general improvements.

## Upgrading

If you're upgrading from 6.1.x to 8.x.x, follow the below guides in the below order:

  * [Upgrading to API v7.0](https://aptivi.gitbook.io/aptivi/terminaux-manual/breaking-changes/api-v7.0)
  * [Upgrading to API v8.0](https://aptivi.gitbook.io/aptivi/terminaux-manual/breaking-changes/api-v8.0)

If you're upgrading from 7.0.x to 8.x.x, follow [this guide](https://aptivi.gitbook.io/aptivi/terminaux-manual/breaking-changes/api-v8.0).
