# Burg Backup 2.1.0

Burg Backup 2.1.0 focuses on reliable backup of UNC/SMB **network sources**, especially when the share root is visible but permissions differ deeper in the folder tree.

## Changes

- Recursive read-access verification for network backup sources.
- Source-specific SMB credentials with explicit precedence when saved.
- Automatic retry with saved source credentials when the current Windows/SYSTEM session has only partial access.
- Authenticated SMB source sessions stay active for the complete restic run.
- `Test Access (Recursive)` reports inaccessible child items instead of checking only the share root.
- A child ACL problem no longer causes the entire reachable source to be discarded; readable data is backed up and denied items are logged.

Local-source backup, restore, retention, scheduling and destination behavior remain unchanged by the 2.1.0 network-source correction.

## Download

Attach the final release assets before publishing:

- `BurgBackup-2.1.0-x64.msi`
- `BurgBackup-2.1.0-Manual-HE.html`
- `SHA256SUMS.txt`

## Upgrade

Install the 2.1.0 MSI over the existing Burg Backup installation. Do not uninstall first if you want the existing local configuration, keys, state and scheduled-job linkage preserved.

## Reminder

After installing or upgrading, run a backup and perform a test restore. A successful backup status is not a substitute for periodically verifying recovery.
