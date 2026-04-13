+++
date = '2026-04-13T18:25:22+03:00'
title = 'SpecProbe 3.8.1 released with initial FreeBSD support'
+++

SpecProbe is a hardware and software information parser that focuses on cross-platform support to allow .NET applications to get information about your computer's installed hardware, such as hard drives and system memory. We used to support Windows, macOS, and Linux to ensure that a wide range of computers can run applications that use SpecProbe.

This library was written in C# with support for both the regular .NET Framework and the modern .NET framework, given the cross-platform nature of the modern .NET framework.

SpecProbe v3.8.1 is now available, and is made exclusively to support FreeBSD systems. This expands the availability of applications that use SpecProbe v3.8.1 or later to work on FreeBSD systems.

The initial support for FreeBSD is now available as an experimental option for curious developers to try out, but future SpecProbe versions will gradually improve support for all operating systems, such as Windows, macOS, and Linux.

Support for FreeBSD systems is a big milestone for SpecProbe, as we have carefully considered our options for .NET's support for FreeBSD, and the official builds of .NET for FreeBSD are still not available yet. This decision was made based on the results of our experiment [here](https://officialaptivi.wordpress.com/2026/04/08/running-net-10-0-on-freebsd-15-0/).

Alongside the FreeBSD support, this version of SpecProbe incorporates various general improvements to the hardware parser.

You can get this version of SpecProbe [here](https://www.nuget.org/packages/SpecProbe/3.8.1).
