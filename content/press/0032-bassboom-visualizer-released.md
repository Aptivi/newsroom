+++
date = '2026-06-20T17:09:31+03:00'
title = 'BassBoom 1.0.1 released with the visualizer feature'
+++

Since the release of BassBoom version v1.0.0 after having gone through several v0.x releases, we have considered working on this application and its corresponding library both for maintenance work and for general feature additions, according to the support schedule.

This version of the BassBoom application and the Basolia library is available as of today!

![Showcase](https://aptivi.gitbook.io/aptivi/~gitbook/image?url=https%3A%2F%2F3839152226-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FizAJoIbtQw1BdIlE4DBz%252Fuploads%252FN7QJBCoJG17K3C7XbWA4%252Fimage.png%3Falt%3Dmedia%26token%3D5752c565-dcbe-4342-903e-824c9c642a44&width=768&dpr=3&quality=100&sign=c7e25dc7&sv=2)

This is a rather small release, with only one new feature being added to BassBoom's Basolia library and the corresponding CLI application that we are shipping. This new feature is the visualizer feature! It allows you to see how the music is played with the frequency band changes being represented visually. We have showcased this feature earlier, but we are now making it available to the public!

The visualizer feature is available as event handlers in the Basolia library, which allows you to build music players and other sound applications that implement the visualizer. Using sampling data and frequency band data, you can build the band visualizers and the sound oscilloscopes that show you either the loudness of the music or the frequency of the bands in all bands, such as bass, mid, and treble bands.

The BassBoom CLI implements the visualizer and the oscilloscope in one place, which is the visualizer screen that allows you to see how the music is visualized, and you can choose from several different presets (using ARROW UP and DOWN) and modes (using M). We hope you like all of them!

To remind you of the sound bands that we visualize, here are the three bands:

* **Bass bands**: Low-frequency content, such as kick drums and bass instruments
* **Mid bands**: Mid-frequency content, such as voices, pianos, and guitars
* **High bands**: High-frequency content, such as hi-hats and hand percussion

The equalizer adjusts itself according to the volume of the output device, so turn up the software volume for the best experience, but make sure that your hardware volume is adjusted appropriately to avoid hearing damage!

## Installing BassBoom and Basolia

To install BassBoom as an application, read the manual [here](https://aptivi.gitbook.io/aptivi/bassboom-manual/installation/installation-and-upgrade). However, if you're an application developer and want to integrate BassBoom v1.0.1 to your project, read the manual [here](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade).
