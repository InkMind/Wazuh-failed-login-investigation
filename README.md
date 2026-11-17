# SOC Practical Lab 01: Windows Failed Login Investigation

**Role:** Aspiring Tier 1 SOC Analyst  
**Project Type:** Blue Team / Security Monitoring  
**Status:** Initial Evidence Collection Completed – Wazuh Investigation Pending

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

Screenshots documenting the initial Windows evidence collection will be added to the `screen<img width="959" height="505" alt="Screenshot 2026-11-17 181529" src="https://github.com/user-attachments/assets/f147167f-c805-4b2f-8bff-8a385b81bb7f" />
shots` directory.

## 5. Wazuh Investigation

**Status: Pending**

The next phase will involve:

- Verifying Windows agent connectivity.
- Searching for Event ID 4625 in Wazuh.
- Investigating relevant Wazuh alerts.
- Correlating Windows Security events with Wazuh.
- Analysing authentication failure patterns.

## 6. Skills Demonstrated

- Windows Event Viewer
- Windows Security Log Analysis
- Authentication Failure Investigation
- Event ID Analysis
- Basic Incident Documentation
- SIEM Investigation (Wazuh – pending)

## 7. Project Outcome

Initial Windows evidence collection has been completed.

The Wazuh investigation and final incident assessment will be documented as the project progresses.
