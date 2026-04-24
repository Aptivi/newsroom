+++
date = '2026-04-24T22:00:12+03:00'
title = 'Aptivi Development Kit 1.0.2.0 released'
+++

Since the first release of [Aptivi Development Toolkit (ADT)](https://officialaptivi.wordpress.com/2026/03/05/aptivi-development-toolkit-adt-is-now-official/), this toolkit has provided both the vendor-provided actions and the standard actions that make project development management easier. This was developed as a drop-in replacement of the old, legacy shell-script-based build tools for cross-platform support in one codebase.

This toolkit was developed to solve problems related to the old shell-based build system, including double maintenance efforts for the vendor script maintainers, consistency issues, and readability issues that were outlined in the above article.

As of today, we have made Aptivi Development Kit v1.0.2.0 available to the public!

To be more specific, the following changes have been made:

* **Improved project handling**: Central directory management improvements allow improved project folder handling, which makes the development kit be able to more consistently know the project root folder.
* **Help now shows for non-standalone actions when requested with `-h`**: When you pass `-h` or `--help` to any non-standalone action commands, you'll be able to see the help page for that action, even though there is no vendor directory.

## Upgrading ADT in your project

This version of Aptivi Development Toolkit is available as a fixed tag for you to clone as a submodule, with the following command:

```shell
$ git submodule add https://github.com/Aptivi/tools
$ git -C tools checkout v1.0.2.0
```

In case you are upgrading the submodule, you'll have to run the following commands in sequence:

```shell
$ git fetch
$ git pull --recurse-submodule
$ git submodule update --remote
$ git -C tools checkout v1.0.2.0
```

To switch to bleeding edge for the development toolkit, though it's not recommended as an unstable commit might break your build system, use the following command:

```shell
$ git -C tools checkout main
```

