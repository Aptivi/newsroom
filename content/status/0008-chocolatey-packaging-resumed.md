+++
date = '2026-07-01T20:11:58+03:00'
title = 'Chocolatey packaging has resumed'
+++

Earlier, we were having problems with getting the Nitrocid and the BassBoom packages to be pushed to the Chocolatey repository due to problems with the validation pipeline that falsely detected our scripts as failing automated checks. Despite our scripts correctly verifying the checksums for the downloaded WiX installer files, the validation pipeline incorrectly detected that checksum verification wasn't there. This caused us to temporarily halt the Chocolatey package distribution for all our applications until the problem was rectified.

**Starting from today, we are very excited to announce that the problem has been solved, and that the normal distribution will begin to all versions soon.**

The problem lied in the way we've authored the installation script, with the utilization of the PowerShell `switch` statements for both the architecture detection and the checksum selection for the architecture-specific installation package. Due to the way we've implemented the method of choosing the appropriate installer and its corresponding checksum, this confused the script validation pipeline, which caused our packages to fail automated checks because the pipeline incorrectly detected that we didn't include the checksum verification for the downloaded installation file, when in fact we did.

So, we've replaced the `switch` statements and refactored the code so that we directly assign the installer URL for the x64 architecture, then switch to their ARM64 counterparts if the package is being installed in an ARM64 system. This solved our problem, and we were finally able to get the packages to go through the automated validation process, which succeeded.

The normal distribution of Chocolatey packages for both Nitrocid and BassBoom will begin shortly. This will take several hours for the packages to actually become available to download from the Chocolatey repository.

**We fixed this problem with great assistance from the Chocolatey Team who took their time into assisting us with this problem and getting us back into track. Special thanks to the Chocolatey Team!**
