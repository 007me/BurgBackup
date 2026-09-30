# Burg Backup 2.1.6

Burg Backup 2.1.6 adds built-in GitHub release checking and rolls up the email-authentication and restore improvements added since the previous public 2.1.0 release.

## Changes since 2.1.0

### Updates
- Manual **Check for Updates** in Settings.
- Optional automatic GitHub release check, at most once every 24 hours and only while the interactive GUI is open.
- Automatic update checking can be disabled in Settings.
- Burg Backup only notifies. It never downloads or installs a new application version automatically.

### Email alerts
- Provider-neutral SMTP presets and authentication modes.
- Google OAuth 2.0 for Gmail / Google Workspace through the Gmail API.
- Microsoft OAuth 2.0 for Microsoft 365 / Outlook.com through Microsoft Graph `Mail.Send`.
- OAuth refresh-token material is protected locally with Windows DPAPI for scheduled SYSTEM backups.
- SMTP-only fields are hidden while OAuth is selected, while saved SMTP values are preserved for later use.

### Restore
- UNC-safe restore for snapshot roots such as `\\server\share`.
- Mixed snapshots containing both local and UNC sources no longer fail a local restore because of an unrelated UNC root.
- Existing snapshots from earlier Burg Backup versions remain usable and do not need to be recreated.

### Network sources
- The recursive network-source access and SMB credential-selection improvements introduced in 2.1.0 remain unchanged.

## Download

Attach the exact final release assets before publishing:

- `BurgBackup-2.1.6-x64.msi`
- `SHA256SUMS.txt`

Updated manuals may also be attached if they were actually revised for 2.1.6.

## Upgrade

Install the 2.1.6 MSI over the existing Burg Backup installation. Do not uninstall first if you want the existing local configuration, keys, OAuth authorization state, backup state and scheduled-job linkage preserved.

## Update-check behavior

The update checker queries the public GitHub Releases API for `007me/BurgBackup`. Drafts and prereleases are not treated as the latest public release. A newer normal release causes Burg Backup to offer to open the official GitHub release page; installation remains a user/admin decision.

## Reminder

After installing or upgrading, run a backup and perform a test restore. A successful backup status is not a substitute for periodically verifying recovery.
