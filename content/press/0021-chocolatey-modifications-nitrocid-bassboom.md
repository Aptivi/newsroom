+++
date = '2026-05-21T09:23:39+03:00'
title = 'Chocolatey packaging modifications for Nitrocid and BassBoom - WiX installer'
+++

When we first released the Chocolatey packaging for Nitrocid and BassBoom, the packages used to use a loose ZIP file method to install the binaries. While this was our method to install Nitrocid and BassBoom in the past, which we're still using in the present, we felt that consistency mattered because our WinGet manifests point towards the WiX installer.

The WiX installer method, which we've implemented for Nitrocid and BassBoom last year, has proven to be reliable, because it installs a desktop icon and a Start Menu icon to launch Nitrocid and BassBoom easily, just like any other program. This simplifies things and avoids having to memorize the full path to use Nitrocid.

As a result, we have introduced a new installation script for Chocolatey packages that utilizes the new WiX installation method, similar to how we used the installers for the WinGet package installation method. Instead of using loose ZIP files to extract the binaries to a directory, it now uses WiX installation method to install those binaries.

Before, we used to use the `Install-ChocolateyZipPackage` method to install the binaries of Nitrocid and BassBoom. The script looked like this ([source](https://github.com/Aptivi-Packaging/ChocolateyManifests/blob/503ab0f048dc6790a5a8ff5f2e8cae2e4f919a9c/Main/Nitrocid/0.2.0/chocopack/tools/chocolateyInstall.ps1)):

```ps
$ErrorActionPreference = 'Stop';
$toolsDir   = "$(Split-Path -parent $MyInvocation.MyCommand.Definition)"
$pkgName    = "KS"
$url        = "https://github.com/Aptivi/Nitrocid/releases/download/v0.2.0.9/0.2.0.9-bin.zip"
$shacheck   = "8D9D695DB35A4B7C5F65EC3056CBB2FB73FFEB6A20EB7BDE32E966B778127BE0"

Write-Output "<*>: for assumptions, <+> for progress, <-> for error"
Write-Output "<*> Installation directory: $toolsDir"
Write-Output "<*> Package Name: $pkgName"
Write-Output "<*> URL: $url"
Write-Output "<*> Expected SHA256 Sum: $shacheck"
Write-Output "<+> Configuration will be automatically generated on startup."

Install-ChocolateyZipPackage $pkgName $url $toolsDir -ChecksumType "sha256" -Checksum $shacheck
```

While the above method was reliable as we tested it since we were first preparing the Chocolatey packaging years ago, we felt that consistency mattered, because the Chocolatey package and the WinGet package used different installation binaries. Now, the Chocolatey package uses the same method as the WinGet package ([source](https://github.com/Aptivi-Packaging/ChocolateyManifests/blob/a1b82ace76132006b9fdd332137d95c7816b6bb3/Main/Nitrocid/0.2.0/chocopack/tools/chocolateyInstall.ps1)).

```ps
$ErrorActionPreference = 'Stop';
Write-Output "<*>: for assumptions, <+> for progress, <-> for error"

# Prepare the basic variables
$toolsDir   = "$(Split-Path -parent $MyInvocation.MyCommand.Definition)"
$pkgName    = "KS"
$version    = "v0.2.0.9"
Write-Output "<*> Installation directory: $toolsDir"
Write-Output "<*> Package Name: $pkgName ($version)"

# Check the system architecture
$architecture = [System.Runtime.InteropServices.RuntimeInformation]::OSArchitecture
$arch         = switch ($architecture) {
    "X64"   { "x64" }
    "Arm64" { "arm64" }
    Default { "unknown" }
}
Write-Output "<*> Architecture: $arch [$architecture]"
if ($arch -eq "unknown") {
    Throw "<-> Nitrocid doesn't support $architecture"
}

# Determine the URL and the SHA256 sum
$url        = "https://github.com/Aptivi/Nitrocid/releases/download/$version/nitrocid-win-$arch-installer.exe"
$shacheck   = switch ($arch) {
    "x64"   { "926460AB264C98C844BCD438A929E8F29B5026876CDFB725E6B2386B37E403AF" }
    "arm64" { "4B698177F6B909711404E6EF2DA39BDD637CF1423210A055E302A8558E756E16" }
}
Write-Output "<*> URL: $url"
Write-Output "<*> Expected SHA256 Sum: $shacheck"

$packageArgs = @{
  packageName   = $packageName
  fileType      = 'exe'
  url           = $url
  silentArgs    = "/quiet /norestart"
  validExitCodes= @(0, 3010, 1641)
  softwareName  = 'Nitrocid*'
  checksum      = $shacheck
  checksumType  = 'sha256'
}

Write-Output "<+> Starting installation..."
Install-ChocolateyPackage @packageArgs
Write-Output "<+> Installation complete!"
```

You can still install Nitrocid v0.2.0.9 and v0.1.0.76, as well as BassBoom v1.0.0, with the old ZIP method with Chocolatey. However, we invite users to try the new experience by running:

* **Nitrocid**
  * **v0.2.0.9**: `choco install ks --version=0.2.0.9-errata --pre`
  * **v0.1.0.76**: `choco install ks --version=0.1.0.76-errata --pre`
* **BassBoom**
  * **v1.0.0**: `choco install bassboom --version=1.0.0-errata --pre`

We appreciate your feedback and your suggestions.
