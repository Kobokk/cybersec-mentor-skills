# Module 03: Privilege Escalation (Linux & Windows)

## Core Objective

Elevate an initial low-privilege shell (`www-data`, standard user) to `root` or `NT AUTHORITY\SYSTEM` by systematically auditing local misconfigurations, trust relationships, and exposed credentials.

## Phase 0: Immediate Post-Foothold Situational Awareness

Before running automated scripts, gather baseline context manually:
- **Who am I & what can I access?** (`id`, `whoami /all`, `groups`, `hostname`, OS/kernel build).
- **Network & internal services:** (`ss -tulpn` / `netstat -ano`) — look for services bound only to `127.0.0.1` that were invisible from external scans.
- **Running processes:** (`ps aux` / `tasklist /v`) — check processes running as `root`/`SYSTEM` executing custom scripts or binaries.

## Linux Privilege Escalation Checklist

1. **Sudo Rights (`sudo -l`):** Check allowed commands, `NOPASSWD` entries, wildcard arguments, and `LD_PRELOAD` / `env_keep` settings (cross-reference with GTFOBins concepts).
2. **SUID / SGID Binaries (`find / -perm -4000 -type f 2>/dev/null`):** Identify custom binaries or non-standard system binaries running with owner privileges.
3. **Linux Capabilities (`getcap -r / 2>/dev/null`):** Look for binaries with `cap_setuid`, `cap_dac_read_search`, or `cap_net_raw`.
4. **Scheduled Tasks (Cronjobs):** Inspect `/etc/crontab`, `/etc/cron*`, and systemd timers for scripts writable by your user or calling relative paths (`PATH` hijacking).
5. **Credential Hunting:** Check web config files (`wp-config.php`, `.env`), database configs, `.bash_history`, SSH keys (`~/.ssh`), and readable backup files.

## Windows Privilege Escalation Checklist

1. **Token Privileges (`whoami /priv`):** Look for `SeImpersonatePrivilege`, `SeAssignPrimaryTokenPrivilege`, `SeBackupPrivilege`, or `SeDebugPrivilege`.
2. **Service Misconfigurations:** Check for **Unquoted Service Paths** with spaces, weak service binary permissions (writable `.exe`), or modifiable service registry keys.
3. **Scheduled Tasks & Autoruns:** Identify scheduled tasks running as `SYSTEM` that execute scripts/binaries in writable directories.
4. **Stored Credentials & Registry:** Check `AlwaysInstallElevated`, saved credentials (`cmdkey /list`), unattended install XML files, and PowerShell history (`ConsoleHost_history.txt`).

## Anti-Spoiler Guiding Prompts

- **Tier 1:** "You already checked your user permissions—now look at what processes or scheduled jobs `root`/`SYSTEM` runs automatically. Is any file in that chain writable by you?"
- **Tier 2:** "Notice that binary has SUID bit set (or `SeImpersonatePrivilege` enabled). Think about how that binary spawns child processes or handles environment variables."
- **Tier 3:** Provide the exact enumeration command or exploitation sequence and explain the privilege boundary being crossed.
