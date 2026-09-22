+++
date = '2026-09-22T20:41:37+03:00'
title = 'Consolidating GitBook documentation repositories'
+++

In an earlier work where we consolidated version-specific documentation repositories to their own branches in the master repo, such as Terminaux and Nitrocid, we have saved time and effort into having to set up a repository for each new supported version series. This caused new versions of our projects to come out faster, but that didn't solve one problem that we needed to solve, which was a unified documentation repository for each project.

It was made easier by a new feature that GitBook introduced to us, which allowed us to set up a Git project that hosts documentations for all our projects without having to initiate a repository for each project, saving more time.

Starting from today, we have consolidated all GitBook documentation repositories to the following three repositories:

  * `aptivi`: Stores the main homepage for the documentation site, as well as rolling documentation for all our projects. If there is a new project, or if there is a new version series of it, the rolling documentation will be stored there, and stable documentation will be cloned to the stable master repo.
  * `aptivi-stable`: Stores documentation for all supported versions of our projects within our support policy, taken from the rolling documentation, and is not updated for new version series. This is available only for Aptivi projects that support backports.
  * `aptivi-deprecated`: Stores all obsolete documentation for past Aptivi projects that went out of support during the entire lifetime.

This means that documentation repositories like `nitrocid-manual` and `terminaux-manual` have been consolidated to the `aptivi` repository, while repositories like `nks-manual-0.1.0-rtm` and `nks-manual-0.2.0-rtm` have been consolidated to the `aptivi-stable` repository, and all are found in the Aptivi Docs organization on GitHub. GitLab is the primary host, with GitHub aa the mirror, to guarantee synchronization.

You can access the following repositories on GitLab:

  * `aptivi`: https://gitlab.com/aptivi/docs/aptivi
  * `aptivi-stable`: https://gitlab.com/aptivi/docs/aptivi-stable
  * `aptivi-deprecated`: https://gitlab.com/aptivi/docs/aptivi-deprecated

You can also use the GitHub repository mirrors listed below:

  * `aptivi`: https://github.com/Aptivi-Docs/aptivi
  * `aptivi-stable`: https://github.com/Aptivi-Docs/aptivi-stable
  * `aptivi-deprecated`: https://github.com/Aptivi-Docs/aptivi-deprecated

The GitBook site that we maintain is still intact, though. This is done as part of improving our project documentations, which we keep working on for each new release of our projects.
