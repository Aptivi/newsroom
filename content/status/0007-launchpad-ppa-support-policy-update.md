+++
date = '2026-06-29T10:53:53+03:00'
title = 'Launchpad PPA support policy update'
+++

When we restarted the distribution of Launchpad PPA packages with new PPAs that pertain to each of our supported applications, we have done careful considerations so that the packages are always available for those running Ubuntu 24.04 LTS Noble Numbat or newer. The libc6 updates were the main factor, and we needed to make sure that our packages remain installable without relying on external APT repositories for clean installation.

Over time, as Ubuntu versions went end of life, starting from Oracular then Plucky, and soon Questing, our support policy explicitly mentions that we don't provide official support for those who are using our projects on end-of-life versions of Ubuntu. However, the packages were still available for those versions of Ubuntu, which misleads users into thinking that we support end-of-life versions of Ubuntu, which is an impossible situation in normal conditions.

Starting from today, we have updated our support policy regarding the Launchpad PPA software distribution method, where we monitor every supported Ubuntu version for the completion of the product lifecycle. After a Ubuntu version goes end of life, packages that pertain to such version of Ubuntu that are used to install our packages will no longer be available in the same day as the end of life announcement goes live in the official Ubuntu news channels. To put it clearly, once your version of Ubuntu goes end of life, you won't be able to install our applications to your system using this method anymore.

The following Ubuntu distribution versions are affected:

  * Ubuntu 25.10 Questing Quokka
  * Ubuntu 25.04 Plucky Puffin
  * Ubuntu 24.10 Oracular Oriole

Users who are running the above Ubuntu versions will have to upgrade their systems to the latest supported version, which is Ubuntu 26.04 LTS Resolute Raccoon, to be able to install our applications using the Launchpad PPA method. This is to increase awareness in our users towards our support policy in supported versions.

The following Launchpad PPAs will be unavailable for the above end-of-life Ubuntu versions:

  * [BassBoom](https://launchpad.net/~eofla/+archive/ubuntu/bassboom)
  * [Nitrocid](https://launchpad.net/~eofla/+archive/ubuntu/nitrocid)
  * [BskyId](https://launchpad.net/~eofla/+archive/ubuntu/bskyid)

To upgrade your Ubuntu system, please follow the official documentation on how to upgrade your system to the latest supported version. Please disable the above Ubuntu PPAs before starting the upgrade to ensure smooth upgrades, then enable them again once the upgrade finishes.
