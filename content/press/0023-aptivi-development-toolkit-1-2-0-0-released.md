+++
date = '2026-05-31T19:46:02+03:00'
title = 'Aptivi Development Kit (ADT) 1.2.0.0 released'
+++

Since the first release of [Aptivi Development Toolkit (ADT)](https://officialaptivi.wordpress.com/2026/03/05/aptivi-development-toolkit-adt-is-now-official/), this toolkit has provided both the vendor-provided actions and the standard actions that make project development management easier. This toolkit was developed to solve problems related to the old shell-based build system, including double maintenance efforts for the vendor script maintainers, consistency issues, and readability issues.

As of today, we have made Aptivi Development Kit v1.2.0.0 available to the public! This version adds some more new features to shape the bright future of the development toolkit days ahead.

To be more specific, the following changes have been made:

* **Added fetch and pull actions**: You can now fetch and pull changes from the current remote or the specified remote for your repository to synchronize the local repository with the remote one.
* **Added project path switch**: You can now specify a relative or an absolute path to another project either inside the repository or outside the repository with `--path`, as long as said project is using Git as the version control system. This is a stepping stone to shape ADT's bright future.
* **Added commit and push switch**: When you make a conventional commit, you'll be able to push it directly after the commit is successful without having to execute the second command for pushing. This is achieved with a single switch: `-p`
* **General improvements and bug fixes**: We've made several improvements to the development toolkit, as well as the bug fixes to improve stability and reliability of the toolkit, as we are committed to providing high-quality projects.

## Upgrading ADT in your project

This version of Aptivi Development Toolkit is available as a fixed tag for you to clone as a submodule, with the following command:

```shell
$ git submodule add https://github.com/Aptivi/tools
$ git -C tools checkout v1.2.0.0
```

In case you are upgrading the submodule, you'll have to run the following commands in sequence:

```shell
$ git fetch
$ git pull --recurse-submodule
$ git submodule update --remote
$ git -C tools checkout v1.2.0.0
```

To switch to bleeding edge for the development toolkit, though it's not recommended as an unstable commit might break your build system, use the following command:

```shell
$ git -C tools checkout main
```
