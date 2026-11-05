+++
date = '2026-11-05T15:48:08+03:00'
title = 'Nitrocid 0.2.1 - Architectural Restructure'
+++

Since the release of Nitrocid 0.2.0, which was a huge feature release over 0.1.0 to celebrate the new milestone of the operating system simulator, we were focusing on the kernel and its addons that provided extra features to users. This marked as the evolution milestone from Nitrocid 0.0.1 (Kernel Simulator back then) from 2018, which provided a simple and minimal shell that provided a few commands to simulate the kernel, to we have today as an operating system simulator built with textual user interfaces and command-line interfaces.

Powered by Terminaux, Nitrocid has become faster and more reliable, as well as more colorful, to ensure that textual user interfaces become more powerful. Originally a set of libraries that helped shape the foundation of the textual user interface and the true color support for terminals, textual user interfaces became possible to implement easily for your terminal applications, with cross-platform support being one of the main features. This powers The Nitrocid Homepage, the splash screen, and various sets of interactive portions of the kernel.

Nitrocid 0.2.0 introduced a new, bold, attractive design with a reimagined appearance and design of the simulated operating system, with many new features that increase your productivity and customizability. Since that release, we were working on ensuring that Nitrocid stays fast and robust while adding new features at the same time.

Our efforts took a few months, in which it eventually shaped the new release of Nitrocid.

Today, we are very excited to announce the brand new version of Nitrocid!

## Nitrocid 0.2.1 - Architectural Restructure

![Showcase](/newsroom/images/nitrocid-0.2.1-final/001.png)

Welcome to the renewed and the improved Nitrocid, which has become faster and more reliable than before. Since the release of 0.2.0, we were working hard on those improvements, and we are so excited to showcase some of these improvements!

### Improved The Nitrocid Homepage

You can now have a more fluid experience with The Nitrocid Homepage! You won't have to wait until all the RSS feeds load successfully, but you can navigate the homepage while the RSS feeds are still loading. This is part of our commitment to make sure that Nitrocid keeps running smoothly, with many bug fixes to be done across different parts of the kernel. Since the homepage was first introduced in 0.1.1, we were working hard to make it smoother and more fluid, with such improvements.

This improves user experience for those who have an unstable connection or no internet connection. Such users can benefit from this performance improvement.

We've also added consistent scrolling experience to scroll through tens of options, including the arrow buttons that move the highlighted choice up or down by a single click. Mouse wheel can now scroll through options quicker, while you can double-click on an item to open it. The notifications count can also be seen at a glance, so that you can see how many notifications waiting for you to read. Clicking on it allows you to get a list of notifications in a separate TUI.

### Multiple feeds in RSS TUI

![RSS TUI](/newsroom/images/nitrocid-0.2.1-final/002.png)

Earlier, the textual user interface for the RSS reader was very limited and only supported a single feed source, while listing available articles to read. Also, it didn't allow more than a single feed to be added, and the only thing you were allowed to do was to read articles.

Starting from 0.2.1, the RSS TUI has gained multiple advantages, including the ability to read articles from more than one RSS feed. You can add more than a single feed by a single keypress and a URL, and the RSS TUI will do the rest of the work. This way, you'll be able to get access to articles from different sites without having to exit the TUI.

We've not only added a feature where you can refresh a single feed that was chosen to get the latest articles, but you can also refresh all feeds to get more up-to-date news, especially for tech news, from all the feeds. Just add an RSS feed link to the RSS TUI, such as [`https://officialaptivi.wordpress.com/feed`](https://officialaptivi.wordpress.com/feed), and the TUI will do the rest.

### POP mail is back!

![RSS TUI](/newsroom/images/nitrocid-0.2.1-final/003.png)

In an earlier version of Nitrocid when we were still in early access, we removed POP mail as it caused Nitrocid to be unusable in ARM systems, but that was back when we supported Mono installations in Linux systems. As we took that out in Nitrocid 0.1.0 as part of modernization process, we wanted to bring POP mail back. However, due to unexpected events that happened, we weren't able to incorporate it to feature releases of Nitrocid.

Now, we are so happy to announce that you can finally use POP mail! You can use your e-mail address to sign in to your mailbox using the POP3 protocol instead of IMAP and to read messages, as well as sending them in both encrypted and unencrypted formats.

You can use the `popmail` command to get started. Just enter your username and your password (or your application password in some providers like Gmail), and you'll be able to check your messages with this protocol. This works separately from the IMAP mail shell, which is the default protocol when you use `mail`.

## Availability

Nitrocid 0.2.1 is now available, starting **November 5th**, on the following platforms:

  * WinGet (Windows)
  * Chocolatey (Windows)
  * Arch Linux AUR (Linux)
  * Launchpad PPA (Linux, Ubuntu only)
  * Manual download (Windows, macOS, Linux, FreeBSD)

To install Nitrocid 0.2.1, or to upgrade from 0.2.1 RC or 0.2.0, visit [this manual page](https://aptivi.gitbook.io/aptivi/nitrocid-ks-manual/installation-and-maintenance/installing-the-kernel) for platform-specific instructions.

For mod developers, the NuGet package will be available on the official NuGet.org repository under the following versions:

  * Nitrocid.Base (`0.2.1`)
  * Nitrocid.Core (`0.2.1`)

For installation instructions, visit [this manual page](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade) to install or upgrade Nitrocid NuGet packages.
