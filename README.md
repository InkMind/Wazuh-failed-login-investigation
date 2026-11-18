# SOC Practical Lab 01: Windows Failed Login Investigation
![SOC Practical Lab 01 Banner](soc-lab-01-banner.png)

**Role:** Aspiring Tier 1 SOC Analyst  
**Project Type:** Blue Team / Security Monitoring  
**Status:** Investigation Completed

## 1. Project Overview

This project involves investigating failed Windows authentication attempts using Windows Event Viewer and Wazuh.

The objective is to identify failed login events, analyse authentication evidence, investigate suspicious activity, and understand how a SIEM solution detects security events.

## 2. Investigation Environment

- Operating System: Windows
- Hostname: DESKTOP-9RNV8GM
- SIEM: Wazuh
- Log Source: Windows Security Event Logs
- Investigation Tool: Windows Event Viewer

## 3. Initial Evidence Collection

### Event Identification

- Event ID: 4625
- Event Description: An account failed to log on.
- Total Events Identified: 6
- Account Involved: hp
- Logon Type: 2 (Interactive)

### Authentication Failure Details

From one inspected event:

- Failure Reason: Unknown user name or bad password
- Status: 0xC000006D
- Sub Status: 0xC000006A
- Source Network Address: 127.0.0.1

### Preliminary Findings

Six failed authentication events were identified in the Windows Security log.

All six inspected events involved the local Windows account `hp`.

The inspected event showed an incorrect-password status and a localhost source address.

The available evidence does not establish malicious intent or an external attacker.

## 4. Investigation Screenshots

The following screenshots document the initial Windows failed login investigation.

### 4.1 Windows Security Log – Event ID 4625

The Windows Security log was filtered to identify six failed authentication events.

![Windows Security Log](01-security-log-4625.png)

### 4.2 Failed Login Event Details

An individual Event ID 4625 was examined to identify the account involved and the type of authentication attempt.

![Failed Login Details](02-failed-login-details.png.png)

### 4.3 Authentication Failure Information

The authentication failure details were examined to identify the reason for the unsuccessful login.

![Authentication Failure Information](03-authentication-failure.png.png)

### 4.4 Wazuh SIEM Investigation

**1. Wazuh Authentication Failure Evidence**

![Wazuh Authentication Failure](03-wazuh-4625-authentication-failure.png.png.png)

**2. Wazuh Alert Overview**

![Wazuh Alert Overview](04-wazuh-4625-alert.png.png)

**3. Wazuh Alert Details**

![Wazuh Alert Details](05-wazuh-4625-details.png.png)

## 5. Investigation Findings

### Detection Summary

A controlled failed-login attempt was generated on the Windows machine using the temporary account `SOC-Lab-Test`.

The failed authentication event was successfully collected and detected by Wazuh.

### Alert Details

| Field | Value |
|---|---|
| Windows Event ID | 4625 |
| Wazuh Rule ID | 60122 |
| Wazuh Alert Level | 5 |
| Alert Description | Logon Failure - Unknown user or bad password |
| Target Account | SOC-Lab-Test |
| Source Account | hp |
| Logon Type | 2 (Interactive) |
| Source Address | ::1 (IPv6 loopback) |
| Failure Status | 0xc000006d |
| Failure Substatus | 0xc000006a |
| Authentication Package | Negotiate |
| Process | svchost.exe |
| Wazuh Agent | Windows-Laptop |

### Analysis

- Event ID 4625 indicates a failed Windows logon attempt.
- Status 0xc000006d indicates a logon failure.
- Substatus 0xc000006a indicates an incorrect password.
- The source address ::1 represents the local IPv6 loopback address.
- Wazuh successfully generated alert 60122 at severity level 5.

### Investigation Conclusion

The investigation successfully demonstrated how Windows failed-login events can be collected, monitored, and detected using Wazuh.

This was a controlled laboratory simulation, not a confirmed external attack.

## 6. Wazuh Investigation

**Status: Completed**

The Windows endpoint successfully transmitted security events to the Wazuh SIEM.

A controlled failed-login attempt was generated using the temporary account `SOC-Lab-Test`.

Wazuh successfully detected the event and generated the following alert:

- Windows Event ID: 4625
- Wazuh Rule ID: 60122
- Alert Level: 5
- Target Account: SOC-Lab-Test
- Source Address: ::1
- Failure Reason: Incorrect password
- Wazuh Agent: Windows-Laptop

The investigation confirmed that the event originated from a local authentication attempt rather than an external network source.

The activity was a controlled laboratory simulation, not a confirmed malicious attack.

## 7. Skills Demonstrated

- Windows Event Viewer
- Windows Security Log Analysis
- Event ID 4625 Investigation
- Authentication Failure Analysis
- Wazuh SIEM Monitoring
- Security Alert Investigation
- Log Analysis and Correlation
- Incident Documentation
- Basic Incident Response
  
## 8. Project Outcome

## Supporting Documentation

[View SOC Incident Report 001](SOC-Incident-Report-001.md)

Successfully completed a practical Windows failed-login investigation using Windows Event Viewer and Wazuh SIEM.

The investigation demonstrated how Windows authentication failures can be generated, collected, detected, analysed, and documented.

Supporting evidence and the formal SOC incident report are included in this repository.

**Investigation Result: Successful**
