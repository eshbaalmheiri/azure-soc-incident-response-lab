# azure-soc-incident-response-lab
SOC investigation and incident response lab using Azure Data Explorer, KQL, Windows Security Events, and ServiceNow.

# Azure SOC Incident Response Lab

## Overview

This project demonstrates an end-to-end Security Operations Center (SOC) investigation and incident-response workflow using Windows Security Events, Azure Data Explorer, Kusto Query Language (KQL), and ServiceNow.

The lab simulates an account compromise in which repeated authentication failures are followed by a successful login, privilege assignment, and unauthorized privileged-group membership.

The objective was to investigate the activity, correlate security events, reconstruct the attack timeline, document findings, and manage the incident through a simulated containment and remediation workflow.

> **Note:** This is a simulated cybersecurity lab. Accounts, IP addresses, hosts, events, and containment actions are lab data and do not represent a production incident.

## Technologies Used

- Azure Data Explorer
- Kusto Query Language (KQL)
- Windows Security Event Logs
- ServiceNow
- GitHub
- SOC investigation and incident-response methodology

## Incident Scenario

Suspicious authentication activity was identified involving the account:

` sara.khan `

Investigation identified repeated failed authentication attempts originating from:

`203.0.113.77`

against workstation:

`WKSTN-103`

The authentication failures were followed by successful authentication and subsequent privileged activity.

## Key Security Events

| Event ID | Description |
|---|---|
| 4625 | Failed logon |
| 4624 | Successful logon |
| 4672 | Special privileges assigned to new logon |
| 4728 | Member added to a security-enabled global group |

## Investigation Timeline

The investigation reconstructed the following sequence:

1. Nine failed authentication attempts were observed against `sara.khan`.
2. A successful authentication followed the failed attempts.
3. Special privileges were assigned to the new logon.
4. Subsequent activity was observed involving `DC-01`.
5. The account was added to the privileged `SOC-Lab-Admins` group.
6. `powershell.exe` was associated with the privileged-group modification.

This sequence was treated in the lab as a suspected account compromise followed by privilege escalation.

## Incident Response

A Priority 1 incident was documented in ServiceNow.

Simulated containment and remediation included:

- Containing the affected account
- Resetting account credentials
- Removing unauthorized privileged-group membership
- Isolating the affected workstation for investigation
- Flagging the source IP for blocking/investigation
- Reviewing additional authentication and privileged activity

## Repository Contents

This repository will contain:

- KQL hunting queries
- Investigation evidence
- Attack timeline
- ServiceNow incident-response documentation
- SOC incident report
- Architecture/attack-flow diagram

## Skills Demonstrated

- Security log analysis
- KQL threat hunting
- Authentication-event investigation
- Event correlation
- Privilege-escalation investigation
- Attack timeline reconstruction
- Incident triage
- Incident documentation
- Containment and remediation planning
- ServiceNow incident management
