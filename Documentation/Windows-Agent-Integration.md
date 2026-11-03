
# Windows Agent Integration

## Overview

A Windows 11 endpoint was integrated with the Wazuh SIEM environment using the Wazuh Windows Agent.

The agent collects endpoint security events and forwards them to the Wazuh Manager for centralized monitoring, analysis, and alert generation.

## Environment Configuration

| Component | Configuration |
|:---|:---|
| Endpoint OS | Windows 11 |
| Agent Name | Windows-Laptop |
| Agent ID | 001 |
| Wazuh Manager | wazuh-server |
| Agent Status | Active |

## Integration Process

### 1. Wazuh Agent Installation

- Installed the Wazuh Windows Agent on the Windows 11 endpoint.
- Configured the agent to communicate with the Wazuh Manager.
- Completed agent registration and enrollment.

### 2. Agent Connectivity

- Started the Wazuh agent service on Windows.
- Verified that the endpoint successfully connected to the Wazuh Manager.
- Confirmed the agent appeared in the Wazuh Dashboard.

### 3. Windows Event Collection

Configured the endpoint to collect Windows security and PowerShell operational events.

The monitored event channels include:

| Event Channel | Purpose |
|:---|:---|
| Windows Security | Authentication and account activity |
| Microsoft-Windows-PowerShell/Operational | PowerShell script execution logging |

### 4. PowerShell Script Block Logging

Enabled PowerShell Script Block Logging through Windows policy configuration.

The following PowerShell registry policy was used:

```powershell
$path = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging"

New-Item -Path $path -Force | Out-Null

New-ItemProperty -Path $path `
    -Name EnableScriptBlockLogging `
    -PropertyType DWord `
    -Value 1 `
    -Force
```

Verified that Script Block Logging was enabled.

### 5. Event Collection Verification

Generated a controlled PowerShell test script and verified that Windows recorded Event ID `4104`.

The event was subsequently received and indexed by Wazuh.

**Verified Event Details:**

| Field | Value |
|:---|:---|
| Event ID | 4104 |
| Event Channel | Microsoft-Windows-PowerShell/Operational |
| Agent | Windows-Laptop |
| Agent ID | 001 |
| Log Source | EventChannel |

## Outcome

Successfully integrated a Windows 11 endpoint with Wazuh and established centralized collection of Windows Security and PowerShell operational events.

This integration provided the foundation for endpoint monitoring, security event investigation, and custom detection rule development.
