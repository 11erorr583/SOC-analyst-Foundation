# Task 05: Windows Logs & Event Viewer (Event IDs)

**Program:** SOC Analyst Foundations  
**Task:** Week 3, Task 5  
**Completed:** 21 November 2026  
**Focus:** Windows Security logs, authentication events, and Event Viewer

## Objective

Explore Windows Event Viewer, locate authentication-related events in the Security log, identify five important Windows Event IDs, and examine the details recorded for a failed logon event.

## Tools and Environment

| Tool / Platform | Purpose |
|---|---|
| Windows Event Viewer | Viewing and filtering Windows events |
| Windows Security log | Reviewing authentication and security events |
| TryHackMe | Hands-on Windows training |
| Windows virtual machine | Practical lab environment |

## Practical Work

### 1. Explore Event Viewer

Opened Event Viewer and navigated to:

`Event Viewer → Windows Logs → Security`

The Security log contains records of Windows security auditing activity, including logon events.

### 2. Filter authentication events

Created custom views to filter the following Event IDs:

- **4624:** An account was successfully logged on.
- **4625:** An account failed to log on.

The custom view workflow was:

1. Open Windows Logs → Security.
2. Select **Create Custom View**.
3. Enter the required Event ID in the event ID filter.
4. Save the custom view with a descriptive name.

### 3. Five important Event IDs

| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4672 | Special privileges assigned to a new logon |
| 4688 | A new process was created |
| 1102 | The audit log was cleared |

### 4. Failed-logon event investigation

The task report includes an Event Viewer screenshot showing failed authentication events and the event details pane. The recorded fields include:

| Field | Value recorded in the report |
|---|---|
| Event ID | The report's written heading says 4626, while the task and surrounding evidence identify the investigation as 4625 |
| Account Name | Administrator |
| Account Domain | DESKTOP-H457k9l |
| Source Network Address | 192.168.1.45 |
| Source Port | 49321 |

**Evidence note:** The report states that the TryHackMe virtual machine did not generate an Event ID 4625 during the initial investigation. The failed-logon details were documented separately in the report. The written heading on page 15 says Event ID 4626, so the exact event ID should be verified against the original event's General tab before treating the record as confirmed Event ID 4625.

## Findings and Observations

1. Event Viewer provides a central interface for examining Windows event logs.
2. Event ID 4624 records successful logons, while Event ID 4625 records failed logons.
3. Custom Views make repeated filtering of specific Event IDs easier.
4. Authentication event details can include account information, source network address, and source port.
5. Repeated failed logons can be a reason for further investigation, but a single failed event does not by itself prove malicious activity.

## SOC Learning Outcomes

- Navigating Windows Event Viewer.
- Locating Windows Security logs.
- Filtering events by Event ID using Custom Views.
- Recognizing common authentication and process-related Event IDs.
- Reviewing account and network fields in authentication event details.
- Recording evidence limitations and discrepancies during an investigation.

## Training Evidence

The accompanying task report contains TryHackMe screenshots, Event Viewer screenshots, custom-view configuration evidence, and the event details reviewed during the exercise.

## Conclusion

This exercise introduced Windows Security log analysis and the use of Event Viewer to review authentication activity. It provided practice with filtering Event IDs and extracting useful details from log records, foundational skills for a SOC analyst investigating suspicious login behavior.

**Status:** Completed
