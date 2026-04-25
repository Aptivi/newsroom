+++
date = '2026-04-25T19:51:59+03:00'
title = 'Terminaux 7.0.23 - Security Update Advisory'
+++

This release of Terminaux v7.0.23 includes security bug fixes. We advise users to upgrade to this version of the project to ensure that attack vectors are reduced.

# Fixed CVEs list

The below CVEs have been fixed as of this release.

## High severity

* [CVE-2026-33908](https://www.cve.org/CVERecord?id=CVE-2026-33908) - [GHSA-fwvm-ggf6-2p4x](https://github.com/advisories/GHSA-fwvm-ggf6-2p4x): ImageMagick has a Stack Overflow in DestroyXMLTree()
* [CVE-2026-33901](https://www.cve.org/CVERecord?id=CVE-2026-33901) - [GHSA-x9h5-r9v2-vcww](https://github.com/advisories/GHSA-x9h5-r9v2-vcww): ImageMagick has a heap Buffer Overflow in ImageMagick MVG decoder

## Medium severity

* [CVE-2026-33536](https://www.cve.org/CVERecord?id=CVE-2026-33900) - [GHSA-v67w-737x-v2c9](https://github.com/advisories/GHSA-v67w-737x-v2c9): ImageMagick has a heap overflow caused by integer overflow/wraparound in viff encoder on 32-bit builds
* [CVE-2026-34238](https://www.cve.org/CVERecord?id=CVE-2026-34238) - [GHSA-26qp-ffjh-2x4v](https://github.com/advisories/GHSA-26qp-ffjh-2x4v): ImageMagick has an integer overflow in despeckle operation causing a heap buffer overflow on 32-bit builds
* [CVE-2026-33899](https://www.cve.org/CVERecord?id=CVE-2026-33899) - [GHSA-cr67-pvmx-2pp2](https://github.com/advisories/GHSA-cr67-pvmx-2pp2): ImageMagick has a heap-Buffer-Overflow write of a single zero byte when parsing xml
* [CVE-2026-33902](https://www.cve.org/CVERecord?id=CVE-2026-33902) - [GHSA-f4qm-vj5j-9xpw](https://github.com/advisories/GHSA-f4qm-vj5j-9xpw): ImageMagick has a Stack Overflow via Recursive FX Expression Parsing
* [CVE-2026-33905](https://www.cve.org/CVERecord?id=CVE-2026-33905) - [GHSA-pcvx-ph33-r5vv](https://github.com/advisories/GHSA-pcvx-ph33-r5vv): ImageMagick has an out-of-bounds read in sample operation
* [CVE-2026-40169](https://www.cve.org/CVERecord?id=CVE-2026-40169) - [GHSA-5592-p365-24xh](https://github.com/advisories/GHSA-5592-p365-24xh): ImageMagick has a heap buffer overflow (WRITE) in the YAML and JSON encoders
* [CVE-2026-40183](https://www.cve.org/CVERecord?id=CVE-2026-40183) - [GHSA-jvgr-9ph5-m8v4](https://github.com/advisories/GHSA-jvgr-9ph5-m8v4): ImageMagick has a heap buffer overflow when encoding JXL image with a 16-bit float
* [CVE-2026-40310](https://www.cve.org/CVERecord?id=CVE-2026-40310) - [GHSA-pwg5-6jfc-crvh](https://github.com/advisories/GHSA-pwg5-6jfc-crvh): ImageMagick has a heap out-of-bounds write in JP2 encoder
* [CVE-2026-40311](https://www.cve.org/CVERecord?id=CVE-2026-40311) - [GHSA-r83h-crwp-3vm7](https://github.com/advisories/GHSA-r83h-crwp-3vm7): ImageMagick has a heap-use-after-free via XMP profile could result in a crash when printing the values
* [CVE-2026-40312](https://www.cve.org/CVERecord?id=CVE-2026-40312) - [GHSA-5xg3-585r-9jh5](https://github.com/advisories/GHSA-5xg3-585r-9jh5): ImageMagick has an off-by-one error in MSL decoder could result in crash
* [GHSA-98cp-rj9f-6v5g](https://github.com/advisories/GHSA-98cp-rj9f-6v5g): ImageMagick has has a stack-buffer-overflow in MNG encoder with oversized pallete

## Low severity

* [GHSA-q8h3-jv9v-57qx](https://github.com/advisories/GHSA-q8h3-jv9v-57qx): ImageMagick has has an off-by-one origin validation in allows out-of-bounds read in morphology processing
* [GHSA-8vfj-q2cp-5m5j](https://github.com/advisories/GHSA-8vfj-q2cp-5m5j): ImageMagick has a heap buffer overflow read in magnify operation via unrecognized magnify:method value
* [GHSA-w54j-7wpm-crhj](https://github.com/advisories/GHSA-w54j-7wpm-crhj): ImageMagick has a heap-buffer-overflow in FTXT encoder
* [GHSA-x928-4434-crqj](https://github.com/advisories/GHSA-x928-4434-crqj): ImageMagick has a memory leak in PNG encoder when writing a MNG image
* [GHSA-pmpg-6pww-fg6q](https://github.com/advisories/GHSA-pmpg-6pww-fg6q): ImageMagick has out-of-bounds access in ConnectedComponentsImage() via CLI-controlled connected-components:* artifacts

# How to upgrade

To upgrade this project, ensure that you use the appropriate methods to perform this upgrade, such as system-wide package managers (like apt) in case of an installed application or a system-wide library, or project-specific package managers (like NuGet) in case of upgrading this project in your app's source code.