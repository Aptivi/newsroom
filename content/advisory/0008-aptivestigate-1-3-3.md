+++
date = '2026-04-26T14:47:33+03:00'
title = 'Aptivestigate 1.3.3'
+++

This release of Aptivestigate v1.3.3 includes security bug fixes. We advise users to upgrade to this version of the project to ensure that attack vectors are reduced.

# Fixed CVEs list

The below CVEs have been fixed as of this release.

## Medium severity

* [CVE-2026-40021](https://www.cve.org/CVERecord?id=CVE-2026-40021) - [GHSA-4f7c-pmjv-c25w](https://github.com/advisories/GHSA-4f7c-pmjv-c25w): Apache Log4net: Silent log event loss in XmlLayout and XmlLayoutSchemaLog4J due to unescaped XML 1.0 forbidden characters

# How to upgrade

To upgrade this project, ensure that you use the appropriate methods to perform this upgrade, such as system-wide package managers (like apt) in case of an installed application or a system-wide library, or project-specific package managers (like NuGet) in case of upgrading this project in your app's source code.