
# Lab Architecture

## Overview

The Wazuh SIEM home lab was deployed using Oracle VirtualBox, with Wazuh running as a virtual machine and Windows 11 configured as the monitored endpoint.

## Architecture Components

| Component | Description |
|:---|:---|
| Wazuh Manager | Centralized security event collection and analysis |
| Wazuh Dashboard | Interface for monitoring and investigating alerts |
| Windows 11 | Endpoint generating security and PowerShell events |
| Wazuh Agent | Collects and forwards endpoint events |
| Oracle VirtualBox | Virtualization platform hosting the Wazuh VM |

## Monitoring Architecture

```text
+-----------------------------+
|       Windows 11            |
|                             |
|  Windows Security Logs      |
|  PowerShell Event Logs      |
+--------------+--------------+
               |
               v
+-----------------------------+
|       Wazuh Agent           |
|       Agent ID: 001         |
+--------------+--------------+
               |
               v
+-----------------------------+
|       Wazuh Manager         |
|                             |
|  Event Analysis             |
|  Rule Evaluation            |
|  Alert Generation           |
+--------------+--------------+
               |
               v
+-----------------------------+
|       Wazuh Dashboard       |
|                             |
|  Threat Hunting             |
|  Security Event Monitoring  |
|  Alert Investigation        |
+-----------------------------+
```

## Monitoring Capabilities

- Windows authentication monitoring.
- Successful and failed login analysis.
- PowerShell Script Block Logging.
- Custom detection rule evaluation.
- MITRE ATT&CK technique mapping.

## Environment

- SIEM: Wazuh
- Endpoint: Windows 11
- Virtualization: Oracle VirtualBox
- Agent: Wazuh Windows Agent
