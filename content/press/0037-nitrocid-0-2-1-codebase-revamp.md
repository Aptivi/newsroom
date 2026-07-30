+++
date = '2026-07-30T19:14:08+03:00'
title = 'Nitrocid 0.2.1 Codebase Revamp'
+++

When we started working on 0.1.0 back in the summer of 2022, we contemplated splitting the base kernel and the additional features to become separate from each other. After much studying in the middle of the development of 0.1.0, we decided to split them to several smaller portions known as loadable addons.

However, despite our efforts to make Nitrocid more useful, some parts of the codebase remained untouched for years, with some of them dating back as far as when Nitrocid was still in its early alpha stage. Despite their functionality, we felt that those parts of the codebase needed modernization as we're decoupling a couple of functionalities so that they become available for the kernel modifications.

As part of our internal project that focuses on making such functionalities more accessible to a wider range of kernel modifications, we've decided to expand their availability by revamping the codebase of those portions. Instead of inflexible code paths that prevent extensibility and repeated code portions that may introduce conflicts in behavior, we've consolidated those functions, which introduces flexibility.

Nitrocid 0.2.1 Release Candidate, which will be released September 24th, 2026 alongside Terminaux 8.8, will incorporate those changes out of the box, and it will bring a wide variety of breaking changes that your mods will have to adjust to, including adjusting calls to inter-addon communication functions to point to the new namespaces and/or classes, which will be documented early August.

As we're finalizing the preparations for the final release of Nitrocid 0.2.1, we'll be conducting rigorous testing to make sure that those refactors don't introduce new issues. Also, we'll make sure that this revamp will expand across codebases over time during the development of the release candidate, after the successful release of the technical preview of this upcoming version.
