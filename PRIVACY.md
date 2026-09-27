# Privacy

This document describes Burg Backup **2.1.0**.

## Telemetry and analytics

Burg Backup 2.1.0 does **not** contain an author-operated analytics, advertising or telemetry service and does not send usage statistics to the Burg Backup maintainer.

There is no automatic account registration or Burg Backup cloud service.

## Network connections

Burg Backup can communicate with services selected or configured by the user, including:

- SFTP backup destinations through Windows OpenSSH.
- UNC/SMB/NAS destinations and network backup sources.
- User-configured SMTP servers when email alerts are enabled.
- The configured restic repository.

After a repository connection failure, Burg Backup can perform short TCP connection checks to `www.microsoft.com:443` and `www.google.com:443`. These checks are used only to help distinguish a general Internet outage from a repository-specific connection failure; normal successful backups do not perform these extra checks.

## Local information

Burg Backup stores configuration, state, logs, cache and keys under its local ProgramData area. Logs can contain operational information such as computer names, job names, paths, destination information, failure messages and snapshot identifiers.

Passwords are stored in protected form using Windows DPAPI. Settings export intentionally excludes passwords, private SSH keys and machine-protected credentials.

## Backup data

Backup data is sent to the destination selected by the user. The Burg Backup maintainer does not operate an intermediary storage service and does not receive the user's backup contents.
