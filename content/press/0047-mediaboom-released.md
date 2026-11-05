+++
date = '2026-11-05T15:22:27+03:00'
title = 'MediaBoom is now live!'
+++

After months of hard work with all our projects, including Nitrocid, Terminaux, BassBoom, and a brand new project, we're about to announce this project that is a descendant of BassBoom, which was released as a music player library that used MPG123 as the backend for handling MP3 files, as well as several MPEG audio files.

We'll give you some of the background info before announcing the brand new project.

BassBoom was first released as a technical preview in September 2023 to demonstrate how .NET could play MPEG media files in a cross-platform way without any friction. We had to explore native libraries, and we've chosen MPG123 as the library that handles MPEG audio files, as a way to start small. Then, BassBoom was released as a stable version back in 2024, with more versions that were released to bring improvements to different components.

We wanted to expand support for more audio files, including potential support for video files, which is why the new project appeared as an experimental branch of BassBoom back in early 2025 before becoming an independent project in August of the same year. Since then, we were working on integrating MPV to the library, but lack of resources prevented us from continuing development until this year.

After countless number of hours spent on ensuring that the new player works properly with MPV, here's when this project saw the light...

## MediaBoom v1.0

![Playing an .m4a file](/newsroom/images/mediaboom-1.0/001.png)

MediaBoom is a new media player application and library that uses MPV as the backend, which not only handles music files, but also handles video files, radio stations, and links to media resources. This allows you to design media player applications without any friction, and is cross-platform with support for Windows, macOS, and Linux.

MediaBoom has almost the same design as BassBoom, except that MediaBoom handles many more multimedia files and resources, and handles a wide variety of formats compared to BassBoom, including M4A, AAC, FLAC, OGG, WAV, and many more audio formats, as well as MP4, AVI, and more video formats.

![Playing a video file in the preview](/newsroom/images/mediaboom-1.0/002.png)

The player application, which runs on your favorite terminal emulator, handles both music and video files, with support for previewing video files. This lets you watch movies and other video files on your terminal. It also automatically scales according to your terminal window, powered by Terminaux.

### Get MediaBoom!

Why not try out MediaBoom today? You can get this application via GitHub, WinGet, Launchpad PPA, Arch Linux AUR, and NuGet!

[Get MediaBoom today](https://github.com/Aptivi/MediaBoom/releases/tag/v1.0.0)
