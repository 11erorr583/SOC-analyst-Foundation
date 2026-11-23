# Task 06: Understanding Logs and Log Analysis

## Overview

| Field | Details |
|---|---|
| Program | SOC Analyst Foundations |
| Task | 06 |
| Topic | Understanding Logs and Log Analysis |
| Learner | Zubia Batool |
| Date | 22 November 2026 |
| Practice platform | TryHackMe |

## Objectives

- Identify common log types and the systems that generate them.
- Understand the structure and security value of Apache web-server access logs.
- Distinguish normal activity from suspicious log entries.
- Understand how baselines help analysts identify unusual activity.

## Hands-on Practice

Completed the following TryHackMe rooms:

- **Investigating Windows**: investigated a Windows machine and answered questions using host and event information.
- **Intro to Logs**: explored log configuration and log rotation settings.

The submitted task evidence records Windows Server 2016 and the local account Administrator in the Investigating Windows exercise. The Intro to Logs exercise included reviewing a logrotate configuration, including 24 compressed log-file rotations and an hourly rotation frequency.

## 1. Log Types and Their Sources

The report identifies these log categories and sources:

| Log type | Example sources |
|---|---|
| Endpoint / host logs | Windows Event Viewer (Application, System, and Security logs), Linux authentication/security logs, macOS Unified Logging |
| Application / web logs | Web servers, web applications, and backend engines |
| Email security logs | Secure email gateways and Microsoft Defender for Office |
| Cloud infrastructure logs | AWS and Azure |
| DNS logs | Internal DNS servers and secure web gateways |
| Network logs | Firewalls, switches, routers, VPNs, and Intrusion Detection Systems (IDS) |

> The task instructions say to list five log types. The submitted report actually documents six categories, so this README preserves all six rather than silently dropping one.

## 2. Apache Web-Server Log Analysis

The report breaks down an example Apache access-log entry into the following fields:

| Field | Example value | Meaning |
|---|---|---|
| Client IP (`%h`) | `192.168.1.45` | Client IP address making the TCP connection |
| Identd (`%l`) | `-` | Remote identd log name; commonly unavailable |
| Auth user (`%u`) | `admin` | Username authenticated through HTTP Basic/Digest authentication |
| Timestamp (`%t`) | `[23/Nov/2026:14:32:10 +0500]` | Date, time, and UTC offset when Apache finished processing the request |
| Request line (`%r`) | `POST /login.php HTTP/1.1` | HTTP method, requested URI, and protocol version |
| Status code (`%>s`) | `200` | HTTP response status returned to the client |
| Response size (`%b`) | `1482` | Response body size in bytes, excluding HTTP headers |
| Referer (`%{Referer}i`) | `https://example.com/index.html` | Page URL the client came from |
| User-Agent (`%{User-agent}i`) | `Mozilla/5.0 ... Chrome/131.0.0.0` | Identifies the browser, operating system, or automated client |

### HTTP status-code notes

- **2xx**: successful response, for example `200 OK`.
- **3xx**: redirect, for example `302 Found`.

## 3. Normal vs. Suspicious Log Activity

### Normal example from the report

The Apache example uses an authenticated `admin` user making a `POST /login.php` request and receiving HTTP `200`. This is an example of a successful web request; whether it is truly benign still depends on the surrounding context and baseline.

### Suspicious example from the report

```text
45.33.32.156 - - [23/Nov/2026:03:41:09 +0500] "GET /login.php?user=admin'%20OR%201=1-- HTTP/1.1" 500 512 "-" "sqlmap/1.8.2#stable (https://sqlmap.org)"
```

**Why it is suspicious:**

- The URL query contains an SQL-injection-style payload: `' OR 1=1--`.
- The request receives HTTP `500`, indicating an internal server error.
- The User-Agent identifies `sqlmap`, an automated SQL-injection testing tool.
- The activity occurs at 03:41, which may be unusual depending on the environment's normal activity.

These indicators warrant investigation. A single log entry is not, by itself, proof that the attack succeeded.

## 4. Baseline in Log Analysis

A **baseline** is a documented profile of normal system, network, and user activity over a representative period. The report gives 14 to 30 days as a typical period.

### Purpose

A baseline provides a reference point for identifying activity that deviates from normal behavior. It helps analysts spot anomalies that may not be identified by known malware signatures alone.

### What analysts can monitor

- Average login attempts
- Normal user working hours
- Typical network bandwidth
- Routine running processes

### Example

If a web server normally handles around 50 login requests per hour during the day, a sudden increase to 2,000 requests at 03:00 may indicate a brute-force attempt or another abnormal event. The analyst should investigate the source, request patterns, affected accounts, and related events before drawing a conclusion.

## Key Takeaways

- Logs come from endpoints, applications, email systems, cloud infrastructure, DNS services, and network devices.
- Apache access logs provide useful context through client IP, timestamp, request, status code, response size, referer, and User-Agent.
- SQL-injection payloads, unexpected server errors, and scanner-identifying User-Agent strings are useful investigation signals.
- Baselines help SOC analysts distinguish routine activity from anomalies.
- Suspicious indicators require correlation and investigation; one event alone does not establish compromise.

## Evidence

The accompanying task report contains TryHackMe screenshots and the written log-analysis exercise. Add the original report or selected screenshots to this folder if you want the evidence available directly in the GitHub repository.

## Tools and Platforms

- TryHackMe
- Windows Event Viewer
- Linux logrotate configuration
- Apache access-log format

## Responsible Use

All practical security learning is conducted in authorized training environments and systems owned by the learner or used with permission.
