+++
date = '2026-05-03T09:27:45+03:00'
title = 'Support Status Change - May 2026'
+++

The support status for our projects has undergone changes following the release of BassBoom version 1.0 on May 2nd. We have studied the support schedule for our projects when it comes to various aspects, such as support for our projects and for operating systems, and we have come to the below results.

The support status for backporting features and maintaining bug fixes across version series, such as Nitrocid v0.1.0, v0.2.0, and v0.2.1, has been created since 2021 when we were experimenting an idea of backporting bug fixes to older version series, and it worked very well to the point that we started implementing it across our projects that needed it, such as Nitrocid, Terminaux, and BassBoom.

## Support status for BassBoom

We have changed the support status for BassBoom and its Basolia library to contain two support lengths:

* Long-term support release: We intend to support BassBoom and its Basolia library for five years if the version is evenly-numbered in the second version component, such as v1.0.0 and v1.2.0.
* Short-term support release: We intend to support BassBoom and its Basolia library for a single year if the version is oddly-numbered in the second version component, such as v1.1.0 and v1.3.0.

This was necessary as the development of v1.0.0 was ongoing, which was put to hold several times until we actually restarted it. Now, BassBoom has the same version support length as Terminaux, with only the difference being the version component that we are focusing on.

So, this means that we intend to support v1.0.0 until May 1st, 2031, five years after the release date. This is a major change that is done for future versions of BassBoom, which have their own release schedule which will be determined later.

We are determined to release future versions of BassBoom to add enhancements and features and to fix bugs that unfold over time and testing sessions.

## Support for operating systems

In addition to the BassBoom support timeline change, we have also re-evaluated the support status for supported operating systems, and found that there were refinements that were needed. We have done the below changes:

* **Windows 11 support change**: We have withdrawn the end of support date, which was supposed to be December 16th, 2032, as Windows 11 continues to thrive, and 2026 is going to be a promising year for Windows 11 as it goes through multiple enhancements.
* **Windows 10 support change**: To support enterprise and other environments that still use Windows 10 as the primary operating system, and to support computers that were made "obsolete" by higher Windows 11 requirements, we have decided to change the support end date from December 17th, 2026, to May 1st, 2031.
* **macOS 15 (Sequoia) support change**: We have decided to end support for all projects that are running in this version of macOS on October 1st, 2027. This is to align with Apple's 3-year support strategy for a single version of macOS.
* **One UI 9.x support change**: By the end of this year, we'll have determined the support duration. Currently, we have added an entry for it, but we didn't determine the support date yet as this version of One UI didn't enter the beta phase yet for the Galaxy S26.

We have also added a new section to the support period documentation that addresses support for FreeBSD systems. A minor version series of FreeBSD tends to be supported as the release schedule declares. Currently, we support FreeBSD v15.0, which was released on December 2nd, 2025, and is expected to end support on September 30th, 2026. Our support of future versions of FreeBSD will use the same strategy.