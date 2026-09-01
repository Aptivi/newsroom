+++
date = '2026-09-01T20:06:06+03:00'
title = 'Improvements made to our libraries for .NET Framework and bundled native libraries'
+++

When we started releasing libraries that bundled native libraries with them, we were bundling them with support for .NET Standard 2.0, which provided compatibility for both the classic .NET Framework and the modern .NET. That work started when BassBoom was under development back in 2023, and our tests were made with the modern .NET framework, as well as the classic one.

However, we discovered that the bundled native libraries that we ship wouldn't get copied over for .NET Framework projects. This bug would cause applications that were built with .NET Framework to fail to either run, as in the case of music players, or to perform some operations, as in the case of sound cues feature in Terminaux-powered applications.

Upon further inspection, the targets file required to copy all native library runtimes for .NET Framework didn't exist in the right directory within the NuGet package. This was the previous definition in the project file for example, BassBoom:

```xml
<None Include="BassBoom.Native.targets" Pack="True" PackagePath="/" />
```

Meanwhile, the targets file was defined as:

```xml
<?xml version="1.0"?>
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Content Include="$(MSBuildThisFileDirectory)\..\runtimes\win-*\native\*.dll">
      <Link>%(FileName)%(Extension)</Link>
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
  </ItemGroup>
  <ItemGroup>
    <Content Include="$(MSBuildThisFileDirectory)\..\runtimes\osx-*\native\*.dylib">
      <Link>%(FileName)%(Extension)</Link>
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
  </ItemGroup>
  <ItemGroup>
    <Content Include="$(MSBuildThisFileDirectory)\..\runtimes\linux-*\native\*.so">
      <Link>%(FileName)%(Extension)</Link>
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
  </ItemGroup>
  <ItemGroup>
    <Content Include="$(MSBuildThisFileDirectory)\..\runtimes\freebsd-*\native\*.so">
      <Link>%(FileName)%(Extension)</Link>
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
  </ItemGroup>
</Project>
```

This definition was obviously wrong, since the files would instead get copied over to the root of the output directory instead of the correct `runtimes` folder. Our tests confirmed this theory, so we fixed this issue by changing the definition of the package path for the targets file to both `build` and `buildTransitive` folders inside the package. The final results looks like this:

```
<None Include="BassBoom.Native.targets" Pack="True" PackagePath="build/BassBoom.Native.targets" />
<None Include="BassBoom.Native.targets" Pack="True" PackagePath="buildTransitive/BassBoom.Native.targets" />
```

After that, we've edited the targets file to make sure that the native library files for all platforms get copied to the correct `runtimes` folder for the .NET Framework project to allow the resulting application to operate correctly. The targets file is now defined like this:

```
<?xml version="1.0"?>
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <RuntimesCopy Include="$(MSBuildThisFileDirectory)\..\runtimes\**\*" />
  </ItemGroup>
  <Target Name="CopyNatives" AfterTargets="Build">
    <Copy SourceFiles="@(RuntimesCopy)"
      DestinationFolder="$(TargetDir)runtimes\%(RecursiveDir)"
      SkipUnchangedFiles="true" />
  </Target>
  <Target Name="PublishNatives" BeforeTargets="ComputeResolvedFilesToPublishList">
    <ItemGroup>
      <ResolvedFileToPublish Include="@(RuntimesCopy)">
        <RelativePath>runtimes\%(RecursiveDir)%(Filename)%(Extension)</RelativePath>
        <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
      </ResolvedFileToPublish>
    </ItemGroup>
  </Target>
</Project>
```

For those who use project publishing facility to release applications, such as the usage of `dotnet publish`, we've also made sure that the native libraries also get pushed to the publish output folder. However, we don't use project publishing facility for our projects at this time, but we may plan to do so in a future version of a project that is expected to release in 2027.

To update our libraries in your console applications, consult the [manual](https://aptivi.gitbook.io/aptivi/csharp-libraries/installation-and-upgrade/upgrade).
