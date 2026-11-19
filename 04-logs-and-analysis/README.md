# 04. Linux Basics and Log Analysis

**Program:** SOC Analyst Foundations  
**Task:** Week 2, Task 4  
**Completed:** 18 November 2026  
**Focus:** Linux command-line fundamentals and log analysis

## Objective

Practice essential Linux commands, become familiar with common system and authentication log locations, and use command-line tools to inspect and filter log entries.

## Learning completed

- Practiced Linux navigation and file-viewing commands: `ls`, `cd`, `cat`, and `tail`.
- Inspected system log output under `/var/log`, including `/var/log/syslog`.
- Used `grep` to filter log entries by keywords.
- Compared successful and failed SSH authentication events in a sample log file.
- Completed the TryHackMe rooms:
  - [Linux Fundamentals Part 1](https://tryhackme.com/room/linuxfundamentalspart1)
  - [Intro to Logs](https://tryhackme.com/room/introtologs)

## Linux log locations

| Log location | Common distribution / service | Purpose |
|---|---|---|
| `/var/log/syslog` | Debian / Ubuntu-based systems | General system activity, daemon events, and non-kernel messages |
| `/var/log/messages` | RHEL / CentOS / Fedora | General system messages |
| `/var/log/auth.log` | Debian / Ubuntu-based systems | Authentication events, SSH logins, sudo activity, and failed login attempts |
| `/var/log/secure` | RHEL / CentOS / Fedora | Authentication and security-related events |
| `/var/log/kern.log` | Common on Debian-based systems | Kernel messages |
| `/var/log/wtmp` | Linux | Binary records of successful logins |
| `/var/log/btmp` | Linux | Binary records of failed login attempts |
| `/var/log/journal/` | systemd-based systems | Persistent journal data managed by systemd-journald |

Log availability and exact filenames can vary by distribution and logging configuration.

## Commands practiced

| Command | Purpose |
|---|---|
| `ls` | List files and directories |
| `cd /var/log` | Navigate to the log directory |
| `cat filename` | Print a file's contents |
| `tail -n 20 /var/log/syslog` | Display the latest 20 lines of the system log |
| `tail -f /var/log/syslog` | Follow new log entries as they are written |
| `grep "Failed" filename` | Find lines containing the word `Failed` |
| `grep "Accepted" filename` | Find lines containing the word `Accepted` |
| `journalctl -xe` | View recent system journal messages with explanatory context |

## Practical log analysis

For the practical filtering exercise, I used a sample file named `log.txt` containing SSH-style authentication events.

```bash
cat log.txt
grep "Accepted" log.txt
grep "Failed" log.txt
```

- `Accepted` entries represented successful authentication events in the sample.
- `Failed` entries represented unsuccessful password attempts.
- The entries included usernames, source IP addresses, timestamps, and SSH-related messages, which are useful fields to review during an initial investigation.

I also inspected recent system messages with:

```bash
tail -n 20 /var/log/syslog
```

**Evidence accuracy note:** The failed-versus-successful authentication filtering shown in the task report was performed against the sample `log.txt` file. The report also shows inspection of `/var/log/syslog`. It does not show a confirmed failed-login search against the machine's actual `/var/log/auth.log`, so this README does not claim that it was performed.

## Key SOC takeaways

1. Authentication logs can help identify repeated failed logins, successful access, and potentially suspicious login patterns.
2. Source IP addresses, usernames, timestamps, and event messages provide useful context when triaging authentication activity.
3. `grep` helps narrow large log files to relevant events, while `tail -f` supports live monitoring.
4. Log paths differ across Linux distributions, so an analyst should confirm which logging service and files are present on the system being investigated.

## Training evidence

TryHackMe completion evidence and terminal screenshots were collected in the task report.

## Scope

This was a foundational learning exercise using training environments and sample log data. It is not a production incident investigation.
