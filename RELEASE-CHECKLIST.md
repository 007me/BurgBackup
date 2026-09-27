# Release checklist

Use this checklist before publishing a Burg Backup release on GitHub.

- [ ] Build the final MSI from the intended source tree.
- [ ] Install it on a clean/test Windows 11 x64 machine or VM.
- [ ] Verify Apps & Features shows one Burg Backup registration with the correct version.
- [ ] Run `Verify-Installation.ps1` locally from the build output and confirm `VERIFICATION OK`.
- [ ] Test a manual backup.
- [ ] Test a scheduled backup running as SYSTEM.
- [ ] Test at least one real file restore and open the restored file.
- [ ] If network sources are used, run `Test Access (Recursive)` and confirm expected ACL behavior.
- [ ] Confirm the final MSI carries the required restic notice and the license/third-party notices applicable to the exact self-contained .NET runtime used by the build.
- [ ] Calculate SHA-256 for the final MSI in PowerShell:

```powershell
Get-FileHash .\BurgBackup-2.1.0-x64.msi -Algorithm SHA256
```

- [ ] Create `SHA256SUMS.txt` containing the hash and exact file name.
- [ ] Create a GitHub Release as a **draft** first.
- [ ] Use tag `v2.1.0` and title `Burg Backup 2.1.0`.
- [ ] Paste the contents of `RELEASE-NOTES-v2.1.0.md` into the release description.
- [ ] Upload the MSI, public Hebrew manual and SHA256SUMS file.
- [ ] Re-read the download names and version numbers before publishing.
- [ ] Publish the release only after every asset is present.
