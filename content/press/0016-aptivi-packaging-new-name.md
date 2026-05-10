+++
date = '2026-05-08T13:11:55+03:00'
title = 'Aptivi Packaging is the new name for Aptivi Choco Pack'
+++

Aptivi Choco Pack is a separate organization that aims to provide a source code for the Chocolatey packaging metadata. This metadata repository covers our repositories, such as Nitrocid and BassBoom. This helps us easily track the packaging state for our applications, such as the package version that corresponds to the release being made. For example, Nitrocid v0.2.0 provides the Chocolatey package that installs this version.

In order to make installation easier for our users without having to depend on external package manager, we have earlier introduced WinGet packaging for both Nitrocid and for BassBoom. Those packages run the Windows Installer package in quiet mode that installs the program automatically. This is based on the fact that Windows 11 ships WinGet by default.

As we are so proud of the results, we have now introduced a new name for the Aptivi Choco Pack organization, called **Aptivi Packaging**!

This organization's rename removes the specificity and embraces the broader view of how we package applications, such as Nitrocid and BassBoom. When we say "specificity", we mean that we've removed references to Chocolatey and Choco in the organization. This clears any confusion over whether this organization is specific to Chocolatey packaging.

This also opens up possibilities for better application packaging, which we will announce as soon as they are made!

## What about the repositories?

We have also renamed the repositories for consistency, since the WinGet manifests repository was named `WinGetManifests`. This is to ensure that the purpose of each repository is clear. The following repositories have been renamed in the URL:

* Chocolatey packaging
  * Old name: https://github.com/Aptivi-Choco-Pack/Packaging
  * New name: https://github.com/Aptivi-Packaging/ChocolateyManifests
* WinGet packaging
  * Old name: https://github.com/Aptivi-Choco-Pack/WinGetManifests
  * New name: https://github.com/Aptivi-Packaging/WinGetManifests

Redirects will work when you attempt to browse to the old URLs listed, but they will take you to the new organization's name and the new repository name. For local clones, however, you'll have to change the remote settings to point to the new remote URLs based on the repository. To do this, just run the following command:

```shell
$ git -C path/to/Packaging remote set-url origin https://github.com/Aptivi-Packaging/ChocolateyManifests
$ git -C path/to/WinGetManifests remote set-url origin https://github.com/Aptivi-Packaging/WinGetManifests
```

After that, verify that fetching the latest changes works by running `git fetch` on the two paths.

## The brighter future

As we are now moving toward the brighter future, we're going ahead to make some more surprising changes that will hopefully make your experience more satisfying, such as introducing new features, improving existing features, and removing unnecessary features.