# Publishing Burg Backup to WinGet

Recommended stable package identity:

- PackageIdentifier: `UdiBurg.BurgBackup`
- PackageName: `Burg Backup`
- Publisher: `Udi Burg`
- InstallerType: `wix` (the distributed file is an MSI authored with WiX; let WingetCreate confirm this from the binary)
- Architecture: `x64`
- Scope: `machine`
- UpgradeBehavior: `install`
- Stable MSI UpgradeCode: `{B680EEF0-AEF9-4279-90D8-14623B67B360}`
- Release installer URL pattern: `https://github.com/007me/BurgBackup/releases/download/v<VERSION>/BurgBackup-<VERSION>-x64.msi`

The package identifier should remain stable after the first accepted submission. `Publisher` and `PackageName` should match the MSI's Apps & Features registration. Burg Backup intentionally uses a new MSI ProductCode for each build/version but keeps the WiX UpgradeCode stable; ensure WingetCreate preserves the detected ProductCode for that exact installer and the stable UpgradeCode/AppsAndFeatures metadata when it generates the manifest. Those fields help WinGet correlate the installed application with the package.

## First publication (2.1.6)

1. Build, install and test the final 2.1.6 MSI.
2. Publish that exact MSI as a normal GitHub Release first. The asset URL must already be public and must not later be replaced by a different build with the same version.
3. Install Microsoft's manifest creator:

```powershell
winget install --id Microsoft.WingetCreate -e
```

4. Start a new manifest from the exact public GitHub release asset:

```powershell
wingetcreate new "https://github.com/007me/BurgBackup/releases/download/v2.1.6/BurgBackup-2.1.6-x64.msi"
```

5. In the interactive prompts use `UdiBurg.BurgBackup` as the package identifier. Verify rather than blindly accepting the detected metadata. Expected values are:

```text
PackageIdentifier : UdiBurg.BurgBackup
PackageVersion    : 2.1.6
Publisher         : Udi Burg
PackageName       : Burg Backup
Architecture      : x64
InstallerType     : wix
Scope             : machine
UpgradeBehavior   : install
UpgradeCode       : {B680EEF0-AEF9-4279-90D8-14623B67B360}
```

WingetCreate should calculate the installer SHA-256 and obtain the ProductCode from the exact published MSI. Do not type a ProductCode from an older build.

Useful metadata for the locale manifest:

```text
PackageLocale          : en-US
License                : Freeware
ShortDescription       : Free Windows backup and restore frontend powered by restic
PackageUrl             : https://github.com/007me/BurgBackup
PublisherUrl           : https://github.com/007me
PublisherSupportUrl    : https://github.com/007me/BurgBackup/issues
ReleaseNotesUrl        : https://github.com/007me/BurgBackup/releases/tag/v2.1.6
```

6. Save the generated manifests locally and review the YAML. In the installer manifest, verify that the ProductCode belongs to the final 2.1.6 MSI and that the Apps & Features correlation data is sensible. If WingetCreate includes the stable UpgradeCode, keep it.
7. Validate before submission:

```powershell
winget validate <path-to-the-generated-manifest-folder>
```

8. Optional but recommended: test the local manifest on a Windows test machine before submitting it:

```powershell
winget settings --enable LocalManifestFiles
winget install --manifest <path-to-the-generated-manifest-folder>
```

Use a clean VM for a true first-install test. Also test an upgrade path separately after a later version exists.

9. Submit the manifest/PR. WingetCreate can open the GitHub sign-in/submission flow interactively. Do not embed a GitHub PAT in a reusable script or document.
10. Wait for the automated checks and possible manual review in `microsoft/winget-pkgs`. After the package is accepted and propagated, verify:

```powershell
winget search --id UdiBurg.BurgBackup -e
winget show --id UdiBurg.BurgBackup -e
```

On a clean test machine:

```powershell
winget install --id UdiBurg.BurgBackup -e
```

## Later releases

Always publish the new GitHub release first, then update the existing WinGet manifest. For example, for 2.1.7:

```powershell
wingetcreate update UdiBurg.BurgBackup `
  --version 2.1.7 `
  --urls "https://github.com/007me/BurgBackup/releases/download/v2.1.7/BurgBackup-2.1.7-x64.msi" `
  --release-notes-url "https://github.com/007me/BurgBackup/releases/tag/v2.1.7" `
  --submit
```

WingetCreate downloads the new installer, updates the URL/hash/version, derives installer metadata and can submit the pull request. Review the generated changes before completing the submission.

After the new manifest is accepted, users can see or install updates with:

```powershell
winget upgrade
winget upgrade --id UdiBurg.BurgBackup -e
```

`winget upgrade --all` can also include Burg Backup along with other installed packages that have updates available.

## Important release rules

- The MSI referenced by WinGet must be byte-for-byte the same MSI published in the GitHub Release.
- Never rebuild and replace an already published version behind the same GitHub URL. Burg Backup's WiX build generates a new MSI ProductCode for every build. If a change is required, increment the Burg Backup version and publish a new release.
- Keep the WiX UpgradeCode stable across releases unless there is an intentional product-family break.
- Keep the PackageIdentifier `UdiBurg.BurgBackup` stable after the first accepted WinGet package.
- Do not publish a WinGet manifest until the corresponding GitHub release asset is public and final.

Once accepted into WinGet, tools such as UniGetUI can discover Burg Backup updates through the WinGet source. Burg Backup's built-in GitHub update checker remains independent and works even for users who did not install through WinGet.
