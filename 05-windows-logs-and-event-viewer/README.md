# 05. Windows Logs & Event Viewer (Event IDs)

**Program:** SOC Analyst Foundations  
**Task:** Task 5  
**Completed:** 21 November 2026  
**Focus:** Windows Security Logs, Event Viewer, and authentication event analysis

## Objective

Explore Windows Event Viewer, locate successful and failed logon events in the Security log, identify important Windows Security Event IDs, and examine the details of a failed-logon event.

## Tools and Environment

| Tool / Platform | Purpose |
|---|---|
| Windows Event Viewer | Reviewing and filtering Windows events |
| Windows Security Log | Investigating authentication and security-related activity |
| TryHackMe | Hands-on Windows investigation practice |
| Windows virtual machine | Lab environment |

## Practical Work

### 1. Exploring Event Viewer

Opened Event Viewer in the Windows virtual machine and navigated to:

`Event Viewer → Windows Logs → Security`

The Security log contains records related to logon activity and other security events.

### 2. Filtering Event IDs 4624 and 4625

Created custom views in Event Viewer to filter the Security log by specific Event IDs:

- **4624:** An account was successfully logged on.
- **4625:** An account failed to log on.

The custom-view workflow was:

1. Open Event Viewer.
2. Navigate to **Windows Logs → Security**.
3. Select **Create Custom View**.
4. Enter the required Event ID in the event filter.
5. Save the custom view with a descriptive name.

The report records that the initial TryHackMe virtual machine did not generate any Event ID 4625 events during the first filtering exercise.

### 3. Important Windows Event IDs

| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4672 | Special privileges assigned to a new logon |
| 4688 | A new process was created |
| 1102 | The audit log was cleared |

These events can help an analyst review authentication activity, privileged logons, process creation, and possible attempts to remove audit evidence.

### 4. Failed-Logon Event Review

The report includes a screenshot of a failed-logon event and records the following details:

| Field | Recorded value |
|---|---|
| Event ID (as shown in the event list) | 4625 |
| Account Name | Administrator |
| Account Domain | DESKTOP-H457k9l |
| Source Network Address | 192.168.1.45 |
| Source Port | 49321 |

These fields provide starting points for investigating which account was targeted and the network source associated with the authentication attempt.

**Evidence accuracy note:** The written caption on page 15 labels this event as Event ID 4626, but the task, screenshot, and event list identify the failed-logon event as 4625. The README records the Event ID shown in the screenshot and explicitly notes the caption inconsistency rather than treating the two labels as interchangeable.

## Findings and SOC Relevance

1. Event Viewer provides visibility into Windows system and security activity.
2. Event ID 4624 records successful logons, while Event ID 4625 records failed logons.
3. Custom Views make it easier to focus an investigation on selected Event IDs.
4. Account names, domains, source addresses, and source ports provide useful context when reviewing authentication events.
5. Repeated failed logons may warrant investigation for password guessing or brute-force activity. A single failed logon alone does not establish an attack.
6. Event ID 1102 is important because clearing the Security audit log may indicate an attempt to remove evidence and should be investigated in context.

## TryHackMe Practice

The task report includes evidence from:

- **Windows Fundamentals 2**
- **Investigating Windows**

The report contains screenshots of the completed rooms and the Windows Event Viewer exercises.

## Key Learning Outcomes

- Navigating Windows Event Viewer.
- Locating and filtering Windows Security logs.
- Understanding common Windows Security Event IDs.
- Reviewing successful and failed authentication events.
- Extracting account and network details from event records.
- Recognizing authentication patterns that may require further SOC investigation.

## Scope

This was a foundational exercise conducted in a training environment. The observations documented here reflect the screenshots and findings recorded in the task report; they should not be interpreted as a production incident investigation.
