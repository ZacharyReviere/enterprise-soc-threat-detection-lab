# 🛡️ Enterprise SOC Threat Detection Lab

![Splunk](https://img.shields.io/badge/Splunk-Enterprise-black)
![Sysmon](https://img.shields.io/badge/Sysmon-Endpoint%20Telemetry-blue)
![Windows](https://img.shields.io/badge/Windows-11-blue)
![SOC](https://img.shields.io/badge/SOC-Threat%20Detection-red)
![SIEM](https://img.shields.io/badge/SIEM-Security%20Monitoring-orange)

## Overview

Built a hands-on Security Operations Center (SOC) environment to collect Windows endpoint telemetry, analyze security events, detect suspicious activity, and create automated security alerts using Splunk Enterprise and Sysmon.

The lab simulates common SOC analyst workflows including log ingestion, threat hunting, detection engineering, dashboard development, and alert creation.

## Architecture

Windows 11 Endpoint → Sysmon → Windows Event Logs → Splunk Enterprise → Detection Searches → SOC Dashboard → Security Alerts

## Technologies

- Splunk Enterprise
- Microsoft Sysmon
- Windows 11
- Windows Event Logs
- PowerShell
- SPL (Search Processing Language)

## Security Monitoring

Configured Splunk to ingest and analyze Windows security and Sysmon telemetry.

Monitored activity including:

- Windows process execution
- PowerShell activity
- Authentication events
- Failed login attempts
- Endpoint security telemetry

## Threat Detection

Created SPL searches to identify suspicious endpoint behavior and authentication activity.

Example detection:

**Repeated Failed Login Detection**

Monitors Windows Security Event ID `4625` and identifies accounts generating multiple failed authentication attempts.

```spl
index=main source="WinEventLog:Security" EventCode=4625
| stats count by Account_Name
| where count >= 3
```

## SOC Dashboard

Developed a SOC Security Monitoring Dashboard in Splunk to visualize endpoint activity and support security investigations.

Dashboard panels include:

- Process Execution Activity
- Suspicious PowerShell Activity

## Security Alerting

Created a scheduled Splunk alert for repeated failed Windows login attempts.

The alert automatically evaluates authentication telemetry and triggers when the detection query returns matching results.

## Skills Demonstrated

- SIEM administration
- Security monitoring
- Log analysis
- Threat detection
- Detection engineering
- SPL querying
- Windows event analysis
- Sysmon telemetry analysis
- Security alert configuration
- SOC dashboard development

## Project Evidence

Screenshots documenting the SOC dashboard, Windows authentication events, and configured detection alert are included in this repository.

## Key Takeaways

This project provided hands-on experience building a basic SOC monitoring workflow from endpoint telemetry collection through detection and alerting. It demonstrates how SIEM platforms can transform raw Windows logs into actionable security detections.

## Lab Screenshots

### SOC Security Monitoring Dashboard
![SOC Security Monitoring Dashboard](Screenshot%202026-08-09%20at%2010.03.47%20PM.png)

### Suspicious PowerShell Activity
![Suspicious PowerShell Activity](Screenshot%202026-08-09%20at%2010.04.04%20PM.png)

### Failed Windows Login Detection
![Failed Windows Login Detection](Screenshot%202026-08-09%20at%2010.45.50%20PM.png)
