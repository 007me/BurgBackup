# Privacy

This document describes Burg Backup **2.1.6**.

## Telemetry and analytics

Burg Backup 2.1.6 does **not** contain an author-operated analytics, advertising or telemetry service and does not send usage statistics to the Burg Backup maintainer.

There is no automatic Burg Backup account registration or Burg Backup cloud service.

## Network connections

Burg Backup can communicate with services selected or configured by the user, including:

- SFTP backup destinations through Windows OpenSSH.
- UNC/SMB/NAS destinations and network backup sources.
- User-configured SMTP servers when SMTP email alerts are enabled.
- Google APIs when the user explicitly connects Gmail / Google Workspace OAuth and email alerts are sent.
- Microsoft identity / Microsoft Graph when the user explicitly connects Microsoft OAuth and email alerts are sent.
- The configured restic repository.
- GitHub's public Releases API for the optional update-check feature.

Automatic update checking is enabled by default in 2.1.6 and can be disabled in Settings. It runs only in the interactive GUI and at most once every 24 hours. A manual check can be requested at any time. Burg Backup sends an unauthenticated HTTPS GET request to the public `007me/BurgBackup` release endpoint and does not include backup contents, repository credentials, email-account credentials or a Burg Backup-generated unique device identifier. As with any normal HTTPS connection, GitHub can observe ordinary connection metadata such as the source IP address and the Burg Backup User-Agent string.

Burg Backup never downloads or installs an application update automatically. When a newer release is found it only offers to open the official GitHub release page in the user's browser.

After a repository connection failure, Burg Backup can perform short TCP connection checks to `www.microsoft.com:443` and `www.google.com:443`. These checks are used only to help distinguish a general Internet outage from a repository-specific connection failure; normal successful backups do not perform these extra checks.

## Local information

Burg Backup stores configuration, state, logs, cache and keys under its local ProgramData area. Logs can contain operational information such as computer names, job names, paths, destination information, failure messages and snapshot identifiers.

Passwords and OAuth refresh-token material are stored in protected form using Windows DPAPI where applicable. Settings export intentionally excludes passwords, private SSH keys and machine-protected credentials/tokens.

The update-check preference and last-check/notified state are stored locally in Burg Backup's UI state file.

## Backup data

Backup data is sent to the destination selected by the user. The Burg Backup maintainer does not operate an intermediary storage service and does not receive the user's backup contents.
