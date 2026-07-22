+++
date = '2026-07-22T20:31:32+03:00'
title = 'Launchpad PPA distribution improvements'
+++

We are very excited to announce that the Launchpad PPA package distribution has undergone a significant improvement over the previous method. Based on our promise to provide you with high-quality software and solutions, we are launching a new, improved method after careful consideration. The reason as to why is below.

In the previous method, we used to build a single PPA package for an oldest Ubuntu series that .NET 10.0 supports, which is Ubuntu 24.04 LTS Noble Numbat. After the build process completes and the packages become available to download, we would then have to manually open Launchpad to copy the packages to the later Ubuntu versions that this version of .NET 10.0 supports.

However, this presented several problems, such as:

  * Earlier iterations used to support all possible versions of Ubuntu that .NET 10.0 supported in official Microsoft's repositories. We had to do that long before the official Ubuntu repositories finally began hosting .NET as of 2022. But, the libc6 version requirement for the Debian package resulted in the package becoming impossible to install in some Ubuntu versions due to this dependency failing.
  * In some cases, we took very long to update the packages for later versions of Ubuntu, because we used to manually copy the packages to the Ubuntu versions that we officially support, as per .NET 10.0's support. This resulted in people who are using Ubuntu 24.04 getting the updated package first before the other PPA users.

In order to address these problems, we have changed our distribution method so that we would be generating a new changelog entry for every supported distribution. We've also decided to split a single job to two parts:

  * Preparation: Our workflow will go on preparing a source package by cloning the repository, restoring NuGet packages for vendoring the dependencies, and making an original source package.
  * Building: Our workflow will then make a Debian source package ready for uploading to the Launchpad PPA, with all the necessary dependencies while restoring missing files.

As a result, we'd be using the same source package for all supported distributions while maintaining compatibility, thus eliminating issues that may be caused by the earlier workflow. Additonally, we would have resolved the update delays, thus making sure that everyone gets the same update across all supported distributions at the same time.
