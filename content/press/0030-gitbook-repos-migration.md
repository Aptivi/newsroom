+++
date = '2026-06-17T15:02:53+03:00'
title = 'Migration of stable GitBook project repositories with main docs repos'
+++

When we started using GitBook for our project documentation starting 2023, we used synchronization with GitHub as a way to store all historical changes made to our documentation since the release of the project. Over time, we started using GitLab to host the documentation repositories, which get mirrored with GitHub. For every stable version of our project, sudh as Nitrocid and Terminaux, a separate repository has been maintained. Currently, we are maintaining the following repositories:

  * `terminaux-manual-8.x`
  * `terminaux-manual-7.x`
  * `terminaux-manual-6.x`
  * `bassboom-1.0.x-manual`
  * `nks-manual-0.1.0-rtm`
  * `nks-manual-0.1.0-sp1`
  * `nks-manual-0.1.0-sp2`
  * `nks-manual-0.1.0-sp3`
  * `nks-manual-0.1.0-sp4`
  * `nks-manual-0.1.0-sp5`
  * `nks-manual-0.1.0-sp6`
  * `nks-manual-0.1.0-sp7`
  * `nks-manual-0.2.0-rtm`
  * `nks-manual-0.2.0-sp1`

However, as an increasing number of versions are ongoing, we have been exploring various strategies to ensure that future documentation get their own branch in a single repository found under the Aptivi Docs GitHub organization. We have tried this with the release of Terminaux 8.1 as a test experiment, and it has been proven to be successful, with the following branches being created in the `terminaux-manual-8.x` repository:

  * x/track/v8.0.x
  * x/track/v8.1.x
  * x/track/v8.2.x
  * x/track/v8.3.x
  * x/track/v8.4.x
  * x/track/v8.5.x

We are now very excited to announce that we will start migrating all the GitBook repositories found in the Aptivi Stable Docs organization! This is done to establish a central place for documentation versions, which will help us in tagging releases that will make it easier to find documentation tailored to a specific version of our projects.

This migration will start beginning June 18th, and is expected to finish before the end of this month. Please note that this is a complete migration, so we won't set up any redirection. This means that all links that point to the repositories mentioned above in the stable docs organization will stop working. Therefore, you'll have to update them manually so they point to:

  * bassboom-manual
  * terminaux-manual
  * nitrocid-ks-manual

We will not only migrate those repositories, but we will also migrate the rolling manuals for specific projects, which makes sure that each project has one repository for the GitBook manual, with several branches pointing to a specific version series (x/rolling) or a specific version (x/stable).
