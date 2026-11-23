# SOC Analyst Foundations

A practical learning portfolio documenting my progression toward a Security Operations Center (SOC) Analyst role. This repository contains structured notes, hands-on exercises, troubleshooting records, and supporting evidence from my foundational cybersecurity studies.

## About

I am building practical skills in defensive security, networking, Linux, virtualized lab environments, and security monitoring. The work is organized by task so that each stage has a clear objective, scope, and outcome.

## Completed Learning Tasks

| Task | Focus | Key topics | Status |
|---|---|---|---|
| [01. SOC Fundamentals](01-soc-fundamentals/README.md) | Cybersecurity introduction and SOC operations | CIA triad, threat/vulnerability/risk, SOC purpose, analyst tiers, Red Team vs Blue Team | Completed |
| [02. Networking for Defenders](02-networking-for-defenders/README.md) | Networking concepts used in defensive security | OSI model, protocols, common ports, DNS resolution, normal vs suspicious traffic | Completed |
| [03. Kali Linux VM Recovery](03-virtualization-and-lab-setup/README.md) | VirtualBox troubleshooting and recovery of an existing Kali Linux VM | Virtual machine configuration corruption, host disk-space exhaustion, recovery using the backup configuration file, storage cleanup, preventive measures | Completed |
| [04. Linux Basics and Log Analysis](04-logs-and-analysis/README.md) | Linux command-line fundamentals and log analysis | `/var/log`, `syslog`, authentication logs, `grep`, `tail`, successful and failed SSH events | Completed |
| [05. Windows Logs & Event Viewer](05-windows-logs-event-viewer/README.md) | Windows Security log investigation | Event Viewer, Event IDs 4624 and 4625, custom views, authentication event details | Completed |

## Repository Structure

```text
SOC-analyst-Foundation/
├── README.md
├── 01-soc-fundamentals/
│   └── README.md
├── 02-networking-for-defenders/
│   └── README.md
├── 03-virtualization-and-lab-setup/
│   └── README.md
├── 04-logs-and-analysis/
│   └── README.md
└── 05-windows-logs-event-viewer/
    └── README.md
```

Supporting task reports and evidence are organized in their corresponding folders.

## Tools and Platforms Used

- TryHackMe
- Oracle VirtualBox
- Kali Linux
- Windows Event Viewer
- Windows Command Prompt and PowerShell
- WHOIS and DNS lookup utilities
- Linux shell utilities: `ls`, `cd`, `cat`, `tail`, `grep`, and `journalctl`

## Completed Work

- Studied the CIA triad and the concepts of threat, vulnerability, and risk.
- Documented the purpose of a Security Operations Center and the responsibilities of L1, L2, and L3 analysts.
- Compared Red Team and Blue Team roles.
- Studied the OSI model, common network protocols and ports, DNS resolution, and examples of normal and suspicious traffic.
- Investigated and recovered an inaccessible Kali Linux virtual machine after host disk-space exhaustion caused its primary VirtualBox configuration file to become empty.
- Documented the root cause, recovery steps, storage cleanup, and preventive measures.
- Practiced Linux navigation and log inspection, reviewed common Linux log locations, and filtered successful and failed authentication events in sample SSH-style logs using `grep`.
- Practiced Windows Event Viewer navigation, created custom views for authentication Event IDs, and reviewed the fields recorded in a failed-logon investigation.

## Scope and Responsible Use

All practical security learning is conducted in authorized training environments and systems I own or have permission to test. No real-world system is targeted without explicit authorization.

## Disclaimer

This repository is a learning portfolio. It is not a claim of professional SOC experience or production incident-response experience. The documentation reflects the work completed in the recorded exercises.
