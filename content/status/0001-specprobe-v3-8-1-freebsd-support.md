+++
date = '2026-04-09T18:53:22+03:00'
title = 'SpecProbe v3.8.1 development update: FreeBSD initial support'
+++

When SpecProbe started as a hardware and software information tool to get information about your hardware and your operating system and its characteristics, it supported three major platforms, which were Windows, macOS, and Linux.

We have started development of SpecProbe v3.8.1 with a promising change that will be the foundation of the next version, which will be v3.9.0, based on the initial experimentation results.

This version of SpecProbe provides initial support for FreeBSD systems, which will finally add the fourth supported platform for applications using this library.

The software information part is done, but the hardware part is not done yet, so we have added a new switch to the demonstration applicaton for you to try out, called `--software-only`, which forces the demo program to only parse software information, along with some tests.

However, the addition of support for FreeBSD does not come without its challenges, because the library loading functions found in `libdl.so` on FreeBSD systems were hidden behind stubs that return an error message, which is `Service unavailable`, according to [`dlerror()`](https://man.freebsd.org/cgi/man.cgi?dlerror), and `ld-elf.so.1` can't be P/invoked as it results in a segmentation fault.

The solution to this challenge was to introduce a tiny wrapper library that makes calls to `dlopen()` and `dlsym()` available, so they work just like in Linux.

We have finally finished adding FreeBSD support for SpecProbe.Software, but the development is not done yet. Stay tuned for a press release once we release this version of SpecProbe.

To get access to SpecProbe demonstration application, you'll need to clone the [source code of SpecProbe](https://github.com/Aptivi/SpecProbe) from GitHub, [install .NET 10.0](https://officialaptivi.wordpress.com/2026/04/08/running-net-10-0-on-freebsd-15-0/) on your FreeBSD 15.0 system, and build the project. Afterwards, run `dotnet path/to/SpecProbe.ConsoleTest.dll`.

Please note that we have only tested this initial support on a FreeBSD 15.0 system.
