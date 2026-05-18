+++
date = '2026-05-18T13:32:19+03:00'
title = 'Nitrocid 0.2.0 SP1 and 0.1.0 SP7 is now available!'
+++

Previously, Nitrocid used to only officially support Linux, macOS, and Windows systems, as we're working towards a goal of ensuring that our applications and projects meet the high quality bar. This kind of support was based on our past work of expanding the reachability of our projects beyond Windows, with this work having started with a Nitrocid version released on [October 2018](https://aptivi.gitbook.io/aptivi/nitrocid-ks-manual/versions-and-compatibility/version-release-notes/v0.0.5.x-series#version-0.0.5.6), then expanded to macOS in a later Nitrocid version.

When we were working on Nitrocid, we wanted to expand the list of supported operating systems in order for our projects to be reachable to users who prefer other operating systems over Windows. To achieve this, we've worked hard over the years to bring this kind of support by integrating automated builds for all supported architectures, including ARM64 and AMD64 architectures over Windows, macOS, and Linux.

Since April 2026, we've been working hard to bring FreeBSD support for [SpecProbe v3.8.1](/newsroom/press/0007-specprobe-3-8-1-released-with-initial-freebsd-support), which enabled other libraries to provide FreeBSD builds for native libraries. With [BassBoom v1.0](/newsroom/press/0015-bassboom-1-0-released), [Terminaux 8.4](/newsroom/press/0019-terminaux-8-4-released), and an updated Magico library, we've managed to enable support for FreeBSD on Nitrocid!

As a result, we're very excited to announce that Nitrocid 0.2.0 Service Pack 1 and Nitrocid 0.1.0 Service Pack 7 versions are now available!

Although those service packs are small, but they form a significant milestone for those who are using FreeBSD, because we've added complete support for FreeBSD to Nitrocid, which allows it to run on such systems without any issues. This release was based on our earlier statement we've made when announcing Terminaux v8.4.

## Availability

As of today, this version of Nitrocid is available on the following package managers:

* Loose binary files as a `.zip` archive (global)
* NuGet package (global)
* WinGet package (Windows)
  * `Aptivi.Nitrocid.0.1.0.x`: for Nitrocid 0.1.0 Service Pack 7
  * `Aptivi.Nitrocid.0.2.0.x`: for Nitrocid 0.2.0 Service Pack 1
* Chocolatey package (Windows)
* Launchpad PPA (Linux)
  * `nitrocid-25`: for Nitrocid 0.1.0 Service Pack 7
  * `nitrocid-28`: for Nitrocid 0.2.0 Service Pack 1
* Arch Linux AUR (Linux)
  * `nitrocid-25`: for Nitrocid 0.1.0 Service Pack 7
  * `nitrocid-28`: for Nitrocid 0.2.0 Service Pack 1

You can follow the installation instructions from the [manual](https://aptivi.gitbook.io/aptivi/nitrocid-ks-manual/installation-and-maintenance/installing-the-kernel).