+++
date = '2026-05-04T07:53:39+03:00'
title = 'Apology regarding BassBoom 1.0 Launchpad PPA'
+++

BassBoom v1.0 sets a big milestone for the project that revolutionizes the way application developers integrate Basolia into their music player or other C# applications in both the classic .NET Framework and the modern .NET software development kit. This version of BassBoom restructures the Basolia library, while increasing reliability of the music player that's already bundled with the project.

When we released BassBoom v1.0, we had expected that the distribution would be complete in one day, seeing as packaging methods have been improved and solidified by introducing the Aptivi Development Toolkit (ADT), as well as auditing the process to verify that nothing went wrong. Right now, this version is available on WinGet and Chocolatey for Windows users, and other packaging methods for users who are using other operating systems.

Unfortunately, the distribution of the Launchpad PPA didn't go well, because there were intermittent infrastructure problems on Canonical's end. For this, we apologize for the lack of availability of BassBoom v1.0 on the Launchpad PPA, and we are working towards making it available.

You'll be able to install BassBoom v1.0 via:

```
$ sudo add-apt-repository ppa:eofla/bassboom
$ sudo apt update
$ sudo apt install bassboom-3
```

This situation was out of our control, and we had to delay the Launchpad PPA distribution by a few days until the problem was solved.
