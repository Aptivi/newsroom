+++
date = '2026-07-17T14:14:15+03:00'
title = 'Aptivi Development Toolkit is now an application'
+++

Since the first release of [Aptivi Development Toolkit (ADT)](https://officialaptivi.wordpress.com/2026/03/05/aptivi-development-toolkit-adt-is-now-official/), this toolkit has provided both the vendor-provided actions and the standard actions that make project development management easier. This toolkit was developed to solve problems related to the old shell-based build system, including double maintenance efforts for the vendor script maintainers, consistency issues, and readability issues.

We have always worked hard to pour our efforts into converting the development toolkit since the release of version 1.2 by implementing several improvements and refactors, as well as a feature in which you're allowed to specify a custom working directory to your chosen project. After several releases of the development toolkit since March 2026, we have now reached a stage where ADT has reached a completely new stage.

Starting from today, July 17th, we are now very excited to announce that Aptivi Development Toolkit is now available as an application!

ADT has become a standalone application by no longer relying on static files with tagged source code snapshots. Instead, we now rely on a proper release procedure that our existing applications, such as Nitrocid, employs. This is now a new method to ensure that ADT is updated effortlessly without having to update submodules separately.

Instead of using submodules in your project, which can be a hassle when managing large projects, you can now install ADT to your computer and build your projects effortlessly. Using a single installation ensures consistency when working with your projects. Additionally, you'll no longer have to write the whole Python command and specify the path to the `adt.py` file; a Python wheel does that automatically for you by providing an `adt` binary.

You don't have to change your vendor script files; they can stay as it is during the migration process.

## Migrating your project

In order to migrate your project from the old-school loose Python script files to the new experience, follow these steps:

1. Make sure that Python and PIP are installed on your system
2. Install the [`aptivi-adt`](https://pypi.org/project/aptivi-adt/) PIP package using `pip install --upgrade aptivi-adt`
3. Verify that ADT works using `adt`
4. Go to the directory of your project
5. Remove the `tools` submodule, which is usually `git submodule deinit tools`, then delete its folder
6. Edit the `.gitmodules` file to remove references to the `tools` submodule
7. Edit all scripts, Makefiles, and other files to point to the new `adt` executable
8. Make a Git commit using `git` and push the changes to the remote

For those who are using Ubuntu, you can utilize the Launchpad PPA under `adt` by executing:

1. `sudo add-apt-repository ppa:eofla/adt`
2. `sudo apt install adt`

We recommend that you use the PIP method if possible, as updates are propagated the instant we release a new version. However, if you wish to include ADT as a build dependency for your PPA, add `adt (>= 1.2.0.3)` to the `Build-Depends` line in your `debian/control` file. Afterwards, go to your PPA, click on **Edit PPA Dependencies**, and add `ppa:eofla/adt` as the dependency.
