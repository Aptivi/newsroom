+++
date = '2026-04-03T15:20:19Z'
title = 'BassBoom is now available via WinGet'
+++

When BassBoom was released, we had spent our continued efforts in making the installation easier for all users by introducing several methods of installation, including the Ubuntu PPA for Ubuntu users, the Chocolatey packaging method for Windows, the PKGBUILD format for Arch Linux, and the NuGet package format for developers who are building apps that are powered by BassBoom.

This cross-platform music player has seen various improvements, including updates to the native [libmpg123](https://www.mpg123.de/) library, updates to Terminaux, and various bug fixes during the lifetime of the application and the Basolia library. The library is responsible for enabling applications to play music that is encoded in MPEG.

Starting from today, BassBoom is now available via WinGet, which is the official Windows package manager made by Microsoft! This was done based on the fact that modern Windows systems come with WinGet without you having to set it up, which makes installation of the BassBoom application easier than never before.

Just execute the below command to install or upgrade BassBoom:

* **Install**: `winget install --id Aptivi.BassBoom --source winget`
* **Upgrade**: `winget upgrade Aptivi.BassBoom`

Please note that, unlike the Nitrocid application that was divided into several versioned packages due to the mod API compatibility, we will treat the WinGet package as an actual application, which means that there won't be versioned packages for version series. This means that there won't be `Aptivi.BassBoom.0.2.x` or `Aptivi.BassBoom.1.0.x`, as the package refers mainly to the music player.

While the Arch Linux packaging method and the Launchpad PPA installation method allow you to install multiple BassBoom version series, this won't happen with WinGet and Windows Installer packages anymore. This is to ensure that users get the latest music player updates.
