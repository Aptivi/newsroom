+++
date = '2026-04-15T21:48:16+03:00'
title = 'Aptivi Development Kit (ADT) 1.0.1.0 released'
+++

Since the first release of [Aptivi Development Toolkit (ADT)](https://officialaptivi.wordpress.com/2026/03/05/aptivi-development-toolkit-adt-is-now-official/), this toolkit has provided both the vendor-provided actions and the standard actions that make project development management easier. This was developed as a drop-in replacement of the old, legacy shell-script-based build tools for cross-platform support in one codebase.

This toolkit was developed to solve problems related to the old shell-based build system, including double maintenance efforts for the vendor script maintainers, consistency issues, and readability issues that were outlined in the above article.

As of today, we have made Aptivi Development Kit v1.0.1.0 available to the public! This version adds improvements on top of the first release, which makes this version the first update made to this toolkit since its inception on March 5th.

To be more specific, the following changes have been made:

* **Added `-d` or `--dry` options for creating commits.** This switch allows you to preview the commit message that the toolkit generates before the actual commit happens. This is used to verify that the commit messages render properly.
* **Added `--self` global parameter.** This allows developers who contribute to ADT to perform Git-related operations to the ADT repository itself, such as creating commits or pushing them to the remote. The target project will refer to ADT instead of the underlying repository, if ADT is cloned as a submodule.
* **Improved push output on completion.** When you run `python tools/adt.py push` from your repository, as soon as the push operation completes, you'll be informed that the push was successful, giving you confirmation that the operation has indeed finished.

## Upgrading ADT in your project

This version of Aptivi Development Toolkit is available as a fixed tag for you to clone as a submodule, with the following command:

```shell
$ git submodule add https://github.com/Aptivi/tools
$ git -C tools checkout v1.0.1.0
```

In case you are upgrading the submodule, you'll have to run the following commands in sequence:

```shell
$ git fetch
$ git pull --recurse-submodule
$ git submodule update --remote
$ git -C tools checkout v1.0.1.0
```

To switch to bleeding edge for the development toolkit, though it's not recommended as an unstable commit might break your build system, use the following command:

```shell
$ git -C tools checkout main
```

