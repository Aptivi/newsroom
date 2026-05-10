+++
date = '2026-05-10T13:18:02+03:00'
title = 'Aptivi Development Kit (ADT) 1.1.0.0 released'
+++

Since the first release of [Aptivi Development Toolkit (ADT)](https://officialaptivi.wordpress.com/2026/03/05/aptivi-development-toolkit-adt-is-now-official/), this toolkit has provided both the vendor-provided actions and the standard actions that make project development management easier. This toolkit was developed to solve problems related to the old shell-based build system, including double maintenance efforts for the vendor script maintainers, consistency issues, and readability issues.

As of today, we have made Aptivi Development Kit v1.1.0.0 available to the public! This version adds improvements on top of the first release, which makes this version the first update made to this toolkit since its inception on March 5th.

To be more specific, the following changes have been made:

* **Added custom actions**: Your projects can now extend the build system on top of the existing actions that ADT provides you so that you can add customized actions that are out of ADT's built-in action scope.
* **Added listing remote branches**: You can now list remote branches by executing ADT with `branches -r` or `branches --remote` as arguments so that you can get a list of remote branches, as well as the local branches, in one output.
* **Attribute and type validation is now enforced**: ADT is now enforcing the conventional commit rules that have been documented [here](https://aptivi.gitbook.io/aptivi/guidelines/contribution-guidelines#git-commits), with attribute and type validation rules. If you have specified a type that requires explanation, you won't be able to make a commit until you provide a body.
* **Push progress is now clearer**: Instead of cryptic codes that are only relevant to developers, you can now see the actual progress that tells you the actual action being made during the push process. Also, the percentage is now clearly shown.
* **Fixed submodule changes causing `git push` fails**: When the push action is executed, ADT now properly excludes submodules in the initial stage while executing `git add -A` in case there are leftovers. This should mitigate the `git push` failures caused by the inclusion of submodules.
* **General improvements and bug fixes**: We've made several improvements to the development toolkit, as well as the bug fixes to improve stability and reliability of the toolkit, as we are committed to providing high-quality projects.

## Upgrading ADT in your project

This version of Aptivi Development Toolkit is available as a fixed tag for you to clone as a submodule, with the following command:

```shell
$ git submodule add https://github.com/Aptivi/tools
$ git -C tools checkout v1.1.0.0
```

In case you are upgrading the submodule, you'll have to run the following commands in sequence:

```shell
$ git fetch
$ git pull --recurse-submodule
$ git submodule update --remote
$ git -C tools checkout v1.1.0.0
```

To switch to bleeding edge for the development toolkit, though it's not recommended as an unstable commit might break your build system, use the following command:

```shell
$ git -C tools checkout main
```