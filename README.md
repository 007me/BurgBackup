# Burg Backup

<p align="center"><img src="assets/Burg-Backup.jpg" alt="Burg Backup" width="120"></p>

**Free Windows backup and restore frontend powered by restic**

> **Freeware · Closed source · Windows 11 x64**

Burg Backup is a Windows desktop application that provides a graphical interface around the restic backup engine. It is intended for users who want encrypted, versioned backups with Windows-oriented scheduling, logging, restore, NAS/SMB and SFTP support without having to build restic command lines manually.

[עברית](README-HE.md) · [Hebrew user manual](https://007me.github.io/BurgBackup/BurgBackup-2.1.0-Manual-HE.html) · [English user manual](https://007me.github.io/BurgBackup/BurgBackup-2.1.0-Manual-EN.html) · [Support policy](SUPPORT.md) · [Security](SECURITY.md) · [Privacy](PRIVACY.md)

Download the installer from the **Releases** section of this repository. For each release, verify the published SHA-256 checksum before installing.

**Current release:** 2.1.6

> GitHub automatically displays “Source code (zip)” and “Source code (tar.gz)” for every release. Those archives contain only the public files in this documentation/distribution repository. **The Burg Backup application source code is not included.**

## Screenshots

A few examples of the Burg Backup interface. Click any screenshot to view it at full size.

### Dashboard

[<img src="assets/screenshots/dashboard.png" alt="Burg Backup Dashboard" width="900">](assets/screenshots/dashboard.png)

| Backup configuration | Scheduling |
| --- | --- |
| [<img src="assets/screenshots/backup.png" alt="Backup configuration" width="420">](assets/screenshots/backup.png) | [<img src="assets/screenshots/schedule.png" alt="Scheduling" width="420">](assets/screenshots/schedule.png) |
| Application settings | Alerts and notifications |
| --- | --- |
| [<img src="assets/screenshots/settings.png" alt="Application settings" width="420">](assets/screenshots/settings.png) | [<img src="assets/screenshots/alerts.png" alt="Alerts and notifications" width="420">](assets/screenshots/alerts.png) |

## Main features

- Three independent backup jobs: SFTP plus two UNC/SMB/NAS jobs with user-defined display names.
- Encrypted restic repositories with versioned snapshots and deduplication.
- File, folder and full-drive source selection, including multiple selections and exclusions.
- Network backup sources with source-specific SMB credentials and recursive access testing.
- Scheduled backups through Windows Task Scheduler, running as SYSTEM.
- Backup queueing so multiple jobs do not run restic concurrently.
- VSS support for suitable local sources.
- Retention policy and Adaptive Storage management.
- Restore browser by repository, date, snapshot, folder and file.
- Hierarchical three-state restore selection in Light and Dark modes.
- UNC-safe restore from mixed local/network-source snapshots.
- Email alerts through SMTP, Gmail/Google Workspace OAuth 2.0, or Microsoft 365/Outlook.com OAuth 2.0.
- Manual and optional once-per-day GitHub release checks; Burg Backup notifies only and never installs updates automatically.
- Live backup and restore status and local logs.
- SFTP and UNC/SMB/NAS destinations.
- Import/export of non-secret settings.
- Light, Dark and Follow Windows appearance modes.

## What's new in 2.1.6

Version 2.1.6 adds **manual and automatic update checks against the official GitHub Releases page**. Automatic checks run only in the interactive GUI, at most once every 24 hours, can be disabled in Settings, and never download or install an update automatically.

Changes since the previous public 2.1.0 release also include:

- Provider-neutral email settings and additional SMTP authentication modes.
- Gmail / Google Workspace OAuth 2.0 using the Gmail API.
- Microsoft 365 / Outlook.com OAuth 2.0 using Microsoft Graph `Mail.Send`.
- OAuth-specific UI cleanup so unused SMTP fields are hidden while OAuth is selected.
- UNC-safe restore for snapshots that contain network-source roots such as `\\server\share`, including mixed local/UNC snapshots.
- Existing 2.1.0 network-source recursive access and SMB credential-selection behavior remains in place.

See [CHANGELOG.md](CHANGELOG.md) for the release history.

## System requirements

- Windows 11 x64.
- Administrator rights for installation and Scheduled Task creation/update.
- No separate .NET installation is required; Burg Backup is distributed as a self-contained Windows application.
- Windows OpenSSH Client is required for SFTP jobs.
- An accessible SFTP server or UNC/SMB/NAS share is required as a backup destination.

Burg Backup 2.1.6 bundles the verified **restic 0.19.1** Windows binary.

## Important backup warning

No backup program should be trusted without testing recovery. After initial setup and periodically afterwards, perform a real restore test and verify that the restored files open correctly.

Burg Backup is provided **AS IS**, without warranty or SLA. See [LICENSE.txt](LICENSE.txt) and [SUPPORT.md](SUPPORT.md).

## Security and secrets

- Repository passwords, SMTP passwords and SMB passwords are protected locally using Windows DPAPI at machine scope.
- Google and Microsoft OAuth refresh-token material is protected locally using Windows DPAPI and is not included in settings export.
- The private SFTP SSH key is stored under the protected Burg Backup ProgramData area.
- Settings export does not include passwords, private SSH keys or machine-protected credentials.
- The bundled restic executable is loaded from the installed Burg Backup Tools directory rather than from PATH.

For security reports, follow [SECURITY.md](SECURITY.md). Do not post passwords, private keys or sensitive backup data in public Issues.

## Privacy

Burg Backup 2.1.6 contains no author-operated telemetry or analytics service. Optional update checking sends a standard unauthenticated HTTPS request to GitHub's public Releases API; it sends no backup data, Burg Backup account information or unique device identifier. See [PRIVACY.md](PRIVACY.md).

## Support model

Burg Backup is a community freeware project maintained on a best-effort basis. Bug reports and feature suggestions are welcome, but there is no guaranteed response time, fix schedule, ongoing development commitment or data-recovery service. See [SUPPORT.md](SUPPORT.md).

## License

Burg Backup is **freeware, not open source**. Personal, educational, non-profit and commercial/internal business use is allowed under the Burg Backup Freeware License. Redistribution is limited to the original unmodified installer under the license terms.

Third-party components remain under their own licenses. Burg Backup uses restic under the BSD 2-Clause License. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

## Relationship to restic

Burg Backup is an independent project and is **not affiliated with, sponsored by, or endorsed by the restic project**. restic is a separate project distributed under its own license.
