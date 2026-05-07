+++
date = '2026-05-07T22:18:42+03:00'
title = 'Update on BassBoom 1.0 Launchpad PPA availability'
+++

Earlier, we have apologized to our users for delaying the Launchpad PPA release of BassBoom v1.0. This situation wasn't taken into account when releasing BassBoom v1.0 on May 2nd, which caused a 5-day delay of the broader availability of BassBoom v1.0 in the Launchpad PPA.

The release of BassBoom v1.0 was done to bring a refactored Basolia library so that future scheduled updates to BassBoom go more smoothly. It also brought improvements and bug fixes to the music player and to the radio station player so that user experience is improved.

This delay was caused by internal issues in the Launchpad's infrastructure, which was unable to start builds for BassBoom v1.0 at the time due to availability issues observed in Launchpad's build farm; so many builders were disabled at the time of the incident.

We are very excited to announce that the BassBoom v1.0 PPA packages are now available to the public after an unexpected delay!

The following systems are supported:

* Supported CPU architectures
  * AMD64: regular PCs with 64-bit support (at least AMD Athlon 64 or Intel Pentium 4 with SSE2)
  * ARM64: Qualcomm Snapdragon laptops, embedded devices (e.g. Raspberry Pi 3), Android devices with Termux + proot-distro ubuntu (e.g. Samsung Galaxy Tab S8)

* Supported operating systems
  * Windows 10 or higher
  * macOS 15 or higher
  * Linux distributions that support .NET 10.0, such as Ubuntu 26.04 LTS Resolute Raccoon
  * FreeBSD 15.0 or higher
  * Android 12 or higher (One UI 4.0 or higher for Samsung devices)

To install BassBoom v1.0 on your Ubuntu system, please execute the below commands:

```
$ sudo add-apt-repository ppa:eofla/bassboom
$ sudo apt update
$ sudo apt install bassboom-3
```

BassBoom v1.0 can be installed with BassBoom v0.2 and v0.1 side-by-side, but only v1.0 is officially supported.
