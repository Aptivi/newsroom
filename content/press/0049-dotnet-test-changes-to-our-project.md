+++
date = '2026-11-13T22:40:09+03:00'
title = '.NET test project changes to our projects'
+++

As we have observed unit test failures for those who are running a Unix system with .NET 11 SDK and Mono installed, along with the target framework set to .NET Framework 4.8 (`net48`), we have decided to evaluate the possible solutions so that `dotnet test` on our projects stays green across all platforms, including macOS, Linux, and FreeBSD.

There was a breaking change that was done to .NET 11 since the first preview was released early this year, which involved changing the behavior of the `dotnet test` command for those who are running test projects on non-Windows platforms with the target of .NET Framework. According to both the [official Microsoft documentation](https://learn.microsoft.com/en-us/dotnet/core/compatibility/sdk/11/mono-launch-target-removed) and the [GitHub pull request](https://github.com/dotnet/sdk/pull/52091) that showed the change in depth, the removal of this testing path was done due to it being an officially unsupported scenario. As a result, .NET 11 SDK now no longer recognizes Mono installations on non-Windows systems, causing runs to either `adt test` or `dotnet test` on our projects to fail.

Earlier, we were unconditionally setting target frameworks to both .NET 10.0 and .NET Framework 4.8 in all test projects for our libraries, and this was when the modern .NET SDK supported this scenario by running Mono with the appropriate path to the test executable. However, users who try to run `adt test` or `dotnet test` with .NET 11 as the default SDK will experience an error similar to the following:

```
/usr/share/dotnet/sdk/11.0.100/Sdks/Microsoft.NET.Sdk/targets/Microsoft.NET.Sdk.targets(1474,5): error NETSDK1243: Project 'Terminaux.Tests' targets .NET Framework, which can only be run on Windows. Either run the project on Windows, change the TargetFramework to a supported .NET TFM (for example, net11.0), or set the RunCommand property explicitly. For more information, see https://learn.microsoft.com/dotnet/core/compatibility/sdk/11/mono-launch-target-removed.
```

We have decided to switch the target framework list so that .NET 10.0 is the only supported framework in non-Windows systems by adding the following constraint [like this](https://github.com/Aptivi/Terminaux/commit/94c1d77e37c8dc2cf8ad3e269fef3ff1d86f69e9):

```xml
<TargetFrameworks>net10.0</TargetFrameworks>
<TargetFrameworks Condition="$([MSBuild]::IsOSPlatform('Windows'))">net10.0;net48</TargetFrameworks>
```

Starting from today, we will begin rolling out this change to all our projects to reflect the officially supported scenarios. This means that we no longer support running unit tests under Mono on Unix systems. However, we won't take our support for Mono itself until we stop supporting .NET Framework in 2031.
