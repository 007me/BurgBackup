# Security policy

## Supported version

Security reports are currently considered for the latest published Burg Backup release. Older releases may not receive fixes.

## Reporting a vulnerability

Please use **GitHub Private Vulnerability Reporting** for this repository when it is enabled:

1. Open the repository's **Security** area.
2. Open **Advisories**.
3. Choose **Report a vulnerability**.

Do not open a public Issue for a vulnerability that could expose credentials, backup contents, privilege boundaries, repository access or code-execution risk.

When reporting, include the affected Burg Backup version, Windows version, steps to reproduce, expected impact and any safe proof-of-concept details that help reproduce the issue. Do not include real passwords, private SSH keys or private backup data.

## Security model highlights

- restic repository data is encrypted with the repository password.
- Burg Backup protects stored passwords with Windows DPAPI at machine scope.
- Sensitive local configuration and key areas use restricted Windows ACLs.
- The bundled restic executable is resolved from the installed Burg Backup Tools directory instead of PATH.
- SFTP private keys are stored in the protected Burg Backup key directory.

These controls reduce risk but do not replace normal endpoint, NAS, account and network security practices.
