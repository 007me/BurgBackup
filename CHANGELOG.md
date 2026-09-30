# Changelog

## 2.1.6
### GitHub update checks
- Added a manual **Check for Updates** action in Settings.
- Added optional automatic update checks against the official `007me/BurgBackup` GitHub Releases feed, at most once every 24 hours.
- Automatic checks run only in the interactive GUI; scheduled/headless backup runs do not contact GitHub for update checking.
- Update checks are notification-only. Burg Backup never downloads or installs an update automatically.
- Automatic notification is shown once per newly detected release; manual checks always report the current result.
- The update check is an unauthenticated HTTPS request to GitHub's public Releases API and sends no Burg Backup account, backup data or unique device identifier.
- Update-check timeouts/failures do not affect backup, restore, scheduling or email delivery.

## 2.1.5
### OAuth UI cleanup and UNC-safe restore
- SMTP-only fields are hidden while Google OAuth or Microsoft OAuth is selected, while their saved values remain available if the user switches back to SMTP credentials.
- The same OAuth field behavior is used in the main Email Alerts page and First Run.
- Restore preserves the exact restic snapshot-tree path for UNC roots such as `\\server\share`.
- Selected restores are grouped by their real top-level restic tree node and restored through restic's `<snapshot>:<subfolder>` syntax.
- Mixed local/UNC snapshots no longer fail a local restore merely because the same snapshot also contains a UNC root.
- Existing snapshots created by earlier Burg Backup versions remain usable; they do not need to be recreated.

## 2.1.4
### Microsoft OAuth 2.0
- Added Microsoft OAuth 2.0 for Microsoft 365 / Exchange Online and Outlook.com email alerts.
- Uses the system browser, PKCE and a Desktop/Public Client flow with no Microsoft client secret.
- Requests delegated Microsoft Graph `Mail.Send` and sends alerts through `/v1.0/me/sendMail`.
- Microsoft refresh-token material is protected locally with machine-scoped Windows DPAPI so scheduled SYSTEM backups can continue to send alerts.

## 2.1.3
### Google OAuth 2.0
- Added end-user Google OAuth 2.0 for Gmail / Google Workspace email alerts.
- Uses the Gmail API with the `gmail.send` scope and explicit account selection.
- The connected Google account becomes the sender identity in OAuth mode.
- Google refresh-token material is protected locally with machine-scoped Windows DPAPI for scheduled SYSTEM backups.
- OAuth tokens are excluded from settings export/import.

## 2.1.1
### Universal SMTP email settings
- Email Alerts became provider-neutral instead of Gmail-only.
- Added presets for Gmail / Google Workspace, Microsoft 365 / Exchange Online, Outlook.com, Yahoo Mail, iCloud Mail, Zoho Mail and Custom SMTP.
- Added Username + password/App Password, Windows credentials and No authentication (SMTP relay) modes.
- SMTP validation follows the selected authentication mode.

## 2.1.0
### Network source recursive access and credential selection
- UNC/SMB backup sources prefer the current Windows/SYSTEM SMB access when it can recursively read the selected source.
- If the share root is visible but a child folder/file is denied and saved source credentials exist, Burg Backup reconnects the share with those credentials before restic starts.
- The authenticated SMB source session remains alive for the complete restic backup.
- `Test Access (Recursive)` performs a recursive read-access test and reports inaccessible paths.
- If NAS-side ACLs still deny individual child items after successful SMB authentication, the source remains in the job so readable data is preserved and denied items remain visible in the backup log.
- Source passwords remain protected with machine-scoped Windows DPAPI and are not exported.

## 2.0.7

- Restore snapshot trees now open explicitly unchecked.
- The indeterminate state is used only when descendants contain a real mix of selected and unselected items.
- Folder selection continues to select/clear every descendant; partial subtrees update parent state correctly.

## 2.0.6

- Restore tree checkboxes use a theme-aware three-state template in Light and Dark modes.
- Checked and partially selected states are clearly visible without changing restore execution behavior.

## 2.0.5

- Restore selection became hierarchical: selecting or clearing a folder applies to every descendant.
- Parents show a partial state when only part of the subtree is selected.
- Fully selected folders restore as a folder path; partial selections restore only selected descendants.

## 2.0.4

- Scroll bars and internal application UI elements follow the selected Burg Backup theme instead of retaining bright stock styling in Dark mode.

## 2.0.3

- The divider between the log list and log contents can be dragged to resize the panes.
- Log contents use word wrap by default, with an option to return to horizontal scrolling.

## 2.0.2

- The left navigation rail expands and collapses with a short eased animation.
- Installer progress messaging explains the possible pre-UAC delay while Windows Installer prepares the installation and may create a System Restore checkpoint.

## 2.0.1

- Burg Backup notification, warning, error and confirmation dialogs follow the selected application theme.
- Native Windows file/folder pickers and UAC dialogs remain controlled by Windows.

## 2.0.0

- Major interface refresh with persistent left navigation, top backup-job selector and collapsible navigation rail.
- Existing backup, restore, configuration, schedule, retention and repository behavior was preserved.
