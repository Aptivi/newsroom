+++
date = '2026-05-19T13:46:37+03:00'
title = 'Terminaux 8.4.0.2 - Security Update Advisory'
+++

This release of Terminaux v8.4.0.2 includes security bug fixes. We advise users to upgrade to this version of the project to ensure that attack vectors are reduced.

# Fixed CVEs list

The below CVEs have been fixed as of this release.

## High severity

* [CVE-2026-46522](https://www.cve.org/CVERecord?id=CVE-2026-46522) - [GHSA-7gg8-qqx7-92g5](https://github.com/advisories/GHSA-7gg8-qqx7-92g5): ImageMagick: Infinite Loop in the MIFF decoder can lead to CPU exhaustion
* [CVE-2026-46520](https://www.cve.org/CVERecord?id=CVE-2026-46520) - [GHSA-36wm-hprc-mcf5](https://github.com/advisories/GHSA-36wm-hprc-mcf5): ImageMagick: Heap Buffer Over-Write in IPL decoder when reading multiple images of different dimensions

## Medium severity

* [CVE-2026-46557](https://www.cve.org/CVERecord?id=CVE-2026-46557) - [GHSA-rcr6-g7jc-f57g](https://github.com/advisories/GHSA-rcr6-g7jc-f57g): ImageMagick: Stack overflow in fx operation
* [CVE-2026-46523](https://www.cve.org/CVERecord?id=CVE-2026-46523) - [GHSA-5r4x-w6p5-222q](https://github.com/advisories/GHSA-5r4x-w6p5-222q): ImageMagick: Use-After-Free in MSL decoder
* [CVE-2026-45359](https://www.cve.org/CVERecord?id=CVE-2026-45359) - [GHSA-vhrh-72hq-w8m7](https://github.com/advisories/GHSA-vhrh-72hq-w8m7): ImageMagick: Out-of-Bounds Read in connected components when the user supplies an invalid keep-top define
* [CVE-2026-46521](https://www.cve.org/CVERecord?id=CVE-2026-46521) - [GHSA-jcqp-6r6f-3mfx](https://github.com/advisories/GHSA-jcqp-6r6f-3mfx): ImageMagick: Heap Buffer Over-Write in MIFF encoder when using LZMA compression
* [CVE-2026-45664](https://www.cve.org/CVERecord?id=CVE-2026-45664) - [GHSA-g5mf-wqq5-vwg6](https://github.com/advisories/GHSA-g5mf-wqq5-vwg6): ImageMagick: Policy Bypass in MNG coder could
* [CVE-2026-45031](https://www.cve.org/CVERecord?id=CVE-2026-45031) - [GHSA-cwpj-h54c-xjpx](https://github.com/advisories/GHSA-cwpj-h54c-xjpx): ImageMagick: Policy Bypass in PSD decoder
* [CVE-2026-45358](https://www.cve.org/CVERecord?id=CVE-2026-45358) - [GHSA-cr6r-hmj8-pr7r](https://github.com/advisories/GHSA-cr6r-hmj8-pr7r): ImageMagick: Out-of-Bounds Read of a single byte in meta encoder
* [CVE-2026-45624](https://www.cve.org/CVERecord?id=CVE-2026-45624) - [GHSA-pfvh-m9xv-8966](https://github.com/advisories/GHSA-pfvh-m9xv-8966): ImageMagick: Heap Buffer Over-Read of a 4 bytes in distort operation
* [CVE-2026-42326](https://www.cve.org/CVERecord?id=CVE-2026-42326) - [GHSA-7wff-wpr6-vmhm](https://github.com/advisories/GHSA-7wff-wpr6-vmhm): ImageMagick: Heap Buffer Over-Read in IPTC encoder
* [CVE-2026-46559](https://www.cve.org/CVERecord?id=CVE-2026-46559) - [GHSA-533m-3wf6-c33v](https://github.com/advisories/GHSA-533m-3wf6-c33v): ImageMagick: Heap Buffer Over-Write of a single byte in the JP2 encoder

# How to upgrade

To upgrade this project, ensure that you use the appropriate methods to perform this upgrade, such as system-wide package managers (like apt) in case of an installed application or a system-wide library, or project-specific package managers (like NuGet) in case of upgrading this project in your app's source code.