# SOC Incident Report 001
## Windows Failed Login Investigation Using Wazuh

**Project:** SOC Practical Lab 01  
**Investigation Date:** 18 November 2026  
**Platform:** Windows 11  
**SIEM:** Wazuh  
**Agent:** Windows-Laptop  
**Analyst:** InkMind  
**Incident Type:** Failed Authentication Attempt  
**Investigation Status:** Completed

---

### 1. Executive Summary

This investigation focused on detecting and analysing a failed Windows authentication attempt using Wazuh SIEM.

A controlled failed-login attempt was generated using a temporary Windows account named `SOC-Lab-Test`. Windows Security Event ID 4625 recorded the failed authentication, and Wazuh successfully collected the event and generated alert 60122.

The investigation confirmed that the login attempt originated locally from the Windows machine and was caused by an incorrect password.

This was a controlled laboratory simulation, not a confirmed malicious attack.

### 2. Objective

- Generate a Windows failed-login event.
- Verify that Windows Security auditing records failed logins.
- Confirm that Wazuh collects the event.
- Analyse the resulting security alert.
- Document the findings and recommended security controls.

### 3. Evidence Collected

| Evidence | Observation |
|---|---|
| Windows Event ID | 4625 |
| Wazuh Rule ID | 60122 |
| Wazuh Alert Level | 5 |
| Alert Description | Logon Failure - Unknown user or bad password |
| Target Account | SOC-Lab-Test |
| Subject Account | hp |
| Logon Type | 2 (Interactive) |
| Source Address | ::1 |
| Failure Status | 0xc000006d |
| Failure Substatus | 0xc000006a |
| Process | svchost.exe |
| Authentication Package | Negotiate |
| Wazuh Agent | Windows-Laptop |

### 4. Technical Analysis

**Event ID 4625 – Failed Logon**

Windows generated Event ID 4625 after the authentication attempt failed.

**Failure Status: 0xc000006d**

Indicates an unsuccessful logon attempt.

**Failure Substatus: 0xc000006a**

Indicates that the password was incorrect.

**Source Address: ::1**

This is the IPv6 loopback address, indicating a local authentication attempt rather than an external network source.

**Wazuh Detection**

Wazuh generated rule 60122 with alert level 5 and the description:

`Logon Failure - Unknown user or bad password`

### 5. Investigation Conclusion

The investigation successfully demonstrated the detection of a Windows failed-login event using Wazuh.

The event was collected from the Windows endpoint, analysed, and classified by Wazuh.

The evidence supports a failed local authentication attempt caused by an incorrect password. No evidence from this controlled test establishes an external attacker or malicious activity.

### 6. Recommended Security Actions

1. Monitor repeated Event ID 4625 occurrences.
2. Investigate unusual authentication patterns and repeated failures.
3. Configure an appropriate account lockout policy.
4. Use strong passwords and multi-factor authentication where available.
5. Continue monitoring Windows authentication events through Wazuh.

### 7. Skills Demonstrated

- Windows Security Event Log analysis
- Event ID 4625 investigation
- Wazuh SIEM monitoring
- Security alert interpretation
- Authentication failure analysis
- Basic incident documentation
- Security evidence collection

### 8. Final Outcome

**Investigation Result:** Successful

Windows failed-login auditing was verified, the controlled authentication failure was generated, and Wazuh successfully detected the event.

**Project:** SOC Practical Lab 01 – Windows Failed Login Investigation
