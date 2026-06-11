+++
date = '2026-06-11T13:08:00+03:00'
title = 'Nitrocid gets updated with the modular Windows installer'
+++

Yesterday, we have announced the modular Windows installer package for Nitrocid v0.2.0 and v0.1.0, as well as the upcoming version of Nitrocid that will add more features to the simulated kernel and its addons, which you can learn more about [here](/newsroom/press/0027-nitrocid-windows-installer-modular). This modularity allows you to install either the lite version of Nitrocid, which only contains the base kernel files, or the full version of Nitrocid, which contains all addons.

This improvement is part of the development plans for v0.2.1, but it's also benefical for both the v0.2.0 and the v0.1.0 version series of Nitrocid, which improves user experience when it comes to installing Nitrocid to Windows systems using the Windows installer method, which we've introduced with the release of Nitrocid v0.1.2 last year.

**Now, we are very excited to announce that this improved Windows installer, which we've made modular, is now available as of versions 0.2.0.10 and 0.1.0.77!**

Earlier Nitrocid versions used not to allow you to choose whether to install the addons or not, but Nitrocid was modular because of a feature that we've introduced during the development of 0.1.0, called the inter-addon communication, which allowed Nitrocid, its addons, and its mods to communicate with another addon without a hard dependency. Now, you can choose whether to include the installation of optional addons or not, during the installation stage.

In case where you need to silently install Nitrocid without any GUI, you can exclude the installation of addons by using the `NitrocidLite=1` directive at the end of the command-line that points to the installer `.exe` file. This will silently install Nitrocid without any extra addons, and omitting that directive means a full installation will be done.

The Chocolatey packages, which already have the improvements that we've introduced earlier as you can learn more about [here](/newsroom/press/0021-chocolatey-modifications-nitrocid-bassboom), and other packages will be available in the next few hours.
