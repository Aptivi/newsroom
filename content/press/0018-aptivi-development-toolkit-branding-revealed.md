+++
date = '2026-05-11T20:00:03+03:00'
title = 'Aptivi Development Toolkit (ADT) Branding Revealed'
+++

Aptivi Development Toolkit (ADT) is a development toolkit that provides you with build hooks and customizable actions to make building your projects easier for other developers. It allows you to turn a complex set of instructions into a single command, such as building projects, cleaning projects, and so on. It supports all kinds of projects, including C# for .NET developers.

However, it was missing a visual identity, which is the official logo for this development toolkit. While this toolkit allows developers to add their build steps and convert them to a single command-line syntax, such as `python tools/adt.py build` in Nitrocid, the visual identity needs to clarify that ADT is a developer's toolkit.

To clarify this visually, we've created a new logo for ADT that you can see below:

![ADT logo](/newsroom/images/adt-brand-new-2026/adt-hero.png)

This new logo earns users an ability to easily recognize that, from the intersecting lines around the Aptivi logo, it's a developer toolkit. This way, users can visually recognize that its aim is to make building and managing the project easier, while giving flexibility to the project developers at the same time by introducing custom actions.

We are excited to announce that this new logo is going to set the toolkit a well-defined future that will eventually be hopefully beneficial and useful for all developers.

The new logos can be found in the updated Aptivi branding kit [here](https://aptivi.github.io/branding/download).

## Installing and upgrading ADT in your project

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
