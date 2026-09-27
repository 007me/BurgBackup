# Changelog

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
