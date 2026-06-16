+++
date = '2026-06-16T18:52:24+03:00'
title = 'Aptivi projects now support FreeBSD 15.1'
+++

On April, our efforts focused on supporting FreeBSD 15.0 for our projects, and they led to successful experiments. Because of them, we're now providing official support for running our projects with FreeBSD 15.0 as the operating system. This is beneficial for those who are running FreeBSD in their computers and wanted to try out our projects.

Today, FreeBSD 15.1 was released, and it was a release that focused on adding security bug fixes, as well as general improvements that are made to the whole operating system. This version of FreeBSD brings updated Wi-Fi network drivers that were based on Linux v7.0, `pkg(8)` support for cloud images using PKGBASE, and Unicode 17.0.0 support. You can now also select a kernel scheduler with `kern.sched.name` at boot time.

We have experimented with .NET 10.0 at the end of an [earlier article](https://officialaptivi.wordpress.com/2026/06/16/upgrading-freebsd-pkgbase-system-from-freebsd-v15-0-to-v15-1/) that was published to Aptivi Blog, and this experiment has been proven to be a successful one, so we've decided to announce something exciting.

We're so excited to announce that, starting from today June 16th, 2026, all Aptivi projects, including Nitrocid; Terminaux; and BassBoom, now officially support FreeBSD 15.1! This means that we can now provide support for those running our projects on this version of FreeBSD, according to the [support timeline](https://aptivi.gitbook.io/aptivi/csharp-libraries/support-periods) that we've described in the official Aptivi project documentation.

Our official support for running our projects on FreeBSD 15.1 will follow the end of life date for the same version, with March 31st, 2027, as the last day of which we'll support our projects on FreeBSD 15.1. After this date, we'll no longer provide official support.

Please note that FreeBSD 14 or lower is not supported.
