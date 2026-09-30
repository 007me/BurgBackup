# Release checklist

Use this checklist before publishing a Burg Backup release on GitHub. Once a version is public, do **not** silently replace its MSI. If a published installer needs to change, publish a new version so GitHub update checks, SHA-256 values and WinGet manifests remain immutable and consistent.

- [ ] Build the final MSI once from the intended source tree.
- [ ] Install it on a clean/test Windows 11 x64 machine or VM.
- [ ] Verify Apps & Features shows one Burg Backup registration with the correct version and publisher `Udi Burg`.
- [ ] Run `Verify-Installation.ps1` locally from the build output and confirm `VERIFICATION OK`.
- [ ] Test a manual backup.
- [ ] Test a scheduled backup running as SYSTEM.
- [ ] Test at least one real file restore and open the restored file.
- [ ] If network sources are used, run `Test Access (Recursive)` and confirm expected ACL behavior.
- [ ] Test Google OAuth and Microsoft OAuth if those release areas changed.
- [ ] Test Settings > Check for Updates. Before publishing 2.1.6 it should report that the installed build is newer than the latest public release; after publishing it should report 2.1.6 as current.
- [ ] Confirm disabling automatic update checking and saving Settings persists after restart.
- [ ] Confirm the final MSI carries the required restic notice and the license/third-party notices applicable to the exact self-contained .NET runtime used by the build.
- [ ] Calculate SHA-256 for the exact final MSI:

```powershell
Get-FileHash .\BurgBackup-2.1.6-x64.msi -Algorithm SHA256
```

- [ ] Create `SHA256SUMS.txt` containing the hash and exact file name.
- [ ] Update `README.md`, `README-HE.md`, `CHANGELOG.md` and `PRIVACY.md` in the public distribution repository.
- [ ] Add `RELEASE-NOTES-v2.1.6.md`.
- [ ] Create the GitHub Release as a **draft** first.
- [ ] Use tag `v2.1.6` and title `Burg Backup 2.1.6`.
- [ ] Paste the contents of `RELEASE-NOTES-v2.1.6.md` into the release description.
- [ ] Upload the exact final `BurgBackup-2.1.6-x64.msi` and `SHA256SUMS.txt`. Upload updated public manuals only if they were actually revised for this release; do not rename an older manual as 2.1.6 without updating it.
- [ ] Re-read all asset names, version numbers and the SHA-256 before publishing.
- [ ] Publish as a normal release, **not** Draft or Pre-release. Burg Backup's `/releases/latest` update check intentionally ignores drafts/prereleases.
- [ ] After publishing, run Burg Backup > Settings > Check for Updates from a 2.1.6 installation and confirm it reports 2.1.6 as latest.
- [ ] Submit/update the WinGet manifest using the same GitHub MSI URL. Never rebuild the MSI between GitHub publication and WinGet submission.
- [ ] For the first WinGet submission, use package ID `UdiBurg.BurgBackup`; verify `InstallerType: wix`, x64/machine scope, the final MSI ProductCode, and stable UpgradeCode `{B680EEF0-AEF9-4279-90D8-14623B67B360}`.
- [ ] Run `winget validate` on the generated manifests and, when practical, test the local manifest in a clean Windows VM before submitting.
