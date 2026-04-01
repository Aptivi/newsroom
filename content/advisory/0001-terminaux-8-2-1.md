+++
date = '2026-04-01T14:34:14+03:00'
title = 'Terminaux 8.2.1 - Security Update Advisory'
+++

This release of Terminaux v8.2.1 includes security bug fixes. We advise users to upgrade to this version of the project to ensure that attack vectors are reduced.

# Fixed CVEs list

The below CVEs have been fixed as of this release.

## Medium severity

* [CVE-2026-33536](https://www.cve.org/CVERecord?id=CVE-2026-33536) - [GHSA-8793-7xv6-82cf](https://github.com/advisories/GHSA-8793-7xv6-82cf): ImageMagick has an Out-of-bounds Write via InterpretImageFilename
* [CVE-2026-33535](https://www.cve.org/CVERecord?id=CVE-2026-33535) - [GHSA-mw3m-pqr2-qv7c](https://github.com/advisories/GHSA-mw3m-pqr2-qv7c): ImageMagick has an Out-of-Bounds write of a zero byte in its X11 display interaction

## Low severity

* [GHSA-9r56-3gjq-hqf7](https://github.com/advisories/GHSA-9r56-3gjq-hqf7): ImageMagick: META reader memory leak in the APP1JPEG input path
* [GHSA-6p22-q7w5-33pg](https://github.com/advisories/GHSA-6p22-q7w5-33pg): ImageMagick has possible memory leak in ASHLAR coder when action fails

# How to upgrade

To upgrade this project, ensure that you use the appropriate methods to perform this upgrade, such as system-wide package managers (like apt) in case of an installed application or a system-wide library, or project-specific package managers (like NuGet) in case of upgrading this project in your app's source code.