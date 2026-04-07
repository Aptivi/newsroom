+++
date = '2026-04-07T23:30:51+03:00'
title = 'Aptivi projects have been removed from Launchpad'
+++

When Nitrocid was still in its early stages, we had poured our efforts to begin supporting the Launchpad PPA method as one of the official installation methods for our project. During the implementation of the method, we had to open a Launchpad project for every single project we had supported at that time, and that was when it was 2021.

Over time, we had started posting announcements to every project's Launchpad page each time we pushed an updated version, but our efforts to keep the announcements consistent had doubled, so we had decided to deprecate the Launchpad projects by advising people to rely on our official Aptivi blog and on our GitHub releases page for our projects in a separate Launchpad announcement.

Since then, we had stopped using our Launchpad projects for announcements and for alternative code hosting channel, since our usage in those projects was pretty minimal. We always use both our blog and our project's GitHub pages as main channels for announcements. New projects weren't entitled to have a Launchpad project page, as our current methods were more suitsble, and our priorities are tailored towards more important plans than trying to maintain our Launchpad projects that may not live long.

In 2025 alone, we have been given a reason, and that was because Launchpad's Bazaar, along with the code browser, was planned to shut down on [December 11th, 2025](https://officialaptivi.wordpress.com/2025/09/14/launchpad-bazaar-will-shutdown-december-2025/). This shut down is currently in effect, and all of Bazaar-hosted code repositories have been permanently deleted.

Our announcement and launch of Aptivi Newsroom has caused us to finally make our decision regarding the Launchpad projects.

**Starting from today, all Aptivi projects have been permanently deleted from Launchpad. Links to those projects on Launchpad will no longer work.**

This deletion means that people who have cloned our code from Launchpad's Git repository, which is separate from the Bazaar ones, will no longer be able to fetch updates from Launchpad. People who plan to clone our code from this repository will no longer be able to do it.

## What are your recommendations?

We advise people to use our project's GitHub to clone its code. We also advise people to only rely on our official announcement channels for our projects, which are:

* Aptivi Blog
* Aptivi Newsroom
* Project's GitHub (if there is one)

Our official channels are regularly updated with any changes that occur to any of Aptivi's projects.

## What are the affected projects?

The following projects, including the abandoned ones, have been affected with this change:

- Addresstigator
- ColorSeq
- Dictify
- Extensification
- GRILO
- Inxi.NET
- LineNumbers
- ManagedWeatherMap
- NameNumerizer
- Namer
- Nitrocid
- ReadLine.Reboot
- SharpLyrics
- ShoutStats
- TermRead
- Uname.NET
- VT.NET
- VisualCard
- Yunikodo

Projects made after February 2023, such as Terminaux and Colorimetry, are not affected with this change, since they don't have an official Launchpad page since the initial release.

## I cloned your project's code from GitHub. Will I no longer be able to use it?

You can still use our project's code from GitHub. Clones, fetches, and pulls will still work if you cloned it from GitHub, as that platform is our primary method of pushing the latest code updates for our projects. You can still contribute to our GitHub repositories by forking our code and making the necessary changes, provided that you're following our [contribution guidelines](https://aptivi.gitbook.io/aptivi/guidelines/contribution-guidelines).

However, if you're using Launchpad Git to fetch our code, Git remote operations will no longer work, and you'll have to change the remote URL to our GitHub project's link and pull all the changes using `git remote set-url origin https://github.com/Aptivi/PROJECT`, assuming that `origin` is the remote name and `PROJECT` is the project name, such as `Nitrocid` and `Terminaux`, and `git fetch ; git pull --recurse-submodules`.
