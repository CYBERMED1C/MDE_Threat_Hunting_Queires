<img width="1254" height="1254" alt="image" src="https://github.com/user-attachments/assets/2ee6f7bf-8b2a-421b-b977-1efc0ddb1ede" />
# MDE Threat Hunting Queries

## Advanced KQL Queries for Microsoft Defender for Endpoint

This repository contains advanced Microsoft Defender for Endpoint threat hunting queries written in Kusto Query Language, also known as KQL. These queries are designed to support defensive cyber operations, incident response, threat hunting, detection engineering, and security monitoring activities.

The purpose of this project is to help defenders identify suspicious activity, validate potential indicators of compromise, enrich investigations, and improve visibility across endpoint telemetry.

## Defensive Use Only

These queries are created for authorized defensive cyber operations only.

They are intended for use by security teams, threat hunters, SOC analysts, incident responders, detection engineers, and other authorized personnel operating inside approved environments.

These queries are not intended to support unauthorized access, exploitation, evasion, persistence, malware deployment, credential theft, or any other offensive or malicious activity.

## Data Sources

The queries in this collection are built around Microsoft Defender for Endpoint Advanced Hunting tables, including but not limited to:

* `DeviceProcessEvents`
* `DeviceNetworkEvents`
* `DeviceFileEvents`
* `DeviceRegistryEvents`
* `DeviceLogonEvents`
* `DeviceImageLoadEvents`
* `DeviceEvents`
* `DeviceTvmSoftwareVulnerabilities`
* `DeviceTvmSoftwareInventory`

Table usage may vary depending on the specific query, available licensing, enabled telemetry, retention period, and tenant configuration.

## Public Reporting and TLP:CLEAR Information

All threat intelligence references, adversary behavior notes, APT-related indicators of compromise, tactics, techniques, procedures, malware names, infrastructure references, and detection ideas used in this repository are based on publicly available information.

Sources may include:

* News articles
* Vendor security reports
* Government cyber advisories
* Public press releases
* Security research blogs
* Public malware analysis reports
* Public incident writeups
* TLP:CLEAR threat intelligence

No classified, restricted, proprietary, confidential, or non-public threat intelligence is intentionally included in this repository.

## APT and IOC Disclaimer

Any references to APT groups, threat actor names, malware families, tools, infrastructure, hashes, domains, IP addresses, registry paths, command-line patterns, or other indicators are included for defensive research and detection purposes only.

APT attribution can change over time. Public reporting may contain incomplete information, overlapping activity clusters, or vendor-specific naming conventions. Queries should be treated as defensive leads, not final proof of attribution.

Before taking action based on a detection, analysts should validate findings with supporting telemetry, timeline analysis, enrichment, and organizational context.

## Query Accuracy

These KQL queries are designed to assist investigations, but they are not guaranteed to identify every malicious event or eliminate all false positives.

Results may vary based on:

* Endpoint telemetry availability
* Sensor health
* Retention period
* Device onboarding status
* Operating system version
* Defender for Endpoint configuration
* Logging visibility
* Environmental baselines
* Legitimate administrative activity
* Software deployment patterns

Every query should be reviewed, tested, tuned, and validated before being used in production detection logic or automated response workflows.

## Recommended Analyst Workflow

When using these queries, analysts should:

1. Review the query logic before running it.
2. Understand the behavior or indicator being hunted.
3. Run the query against a reasonable time window.
4. Validate results against known-good administrative activity.
5. Pivot into related process, file, network, registry, and logon events.
6. Enrich indicators using trusted threat intelligence sources.
7. Document findings, assumptions, and evidence.
8. Tune the query for the local environment.
9. Convert high-confidence logic into detections only after validation.

## Suggested Time Windows

Some queries are designed for short-term triage, while others are better suited for longer historical hunts.

Common hunting windows include:

* Last 24 hours for active investigation
* Last 7 days for recent suspicious behavior
* Last 30 days for campaign-style activity
* Last 90 days when available for historical review

Use the smallest time window that still supports the investigation. Large searches may create noisy results or slow query performance.

## False Positives

Some queries may return legitimate activity, especially in environments with heavy administrative scripting, software deployment tools, remote management platforms, penetration testing activity, help desk tooling, or developer systems.

Common sources of false positives include:

* PowerShell administration
* Remote monitoring and management tools
* Software deployment systems
* Vulnerability scanners
* Backup agents
* Security tools
* IT automation scripts
* Developer build activity
* Internal penetration testing
* Red team assessments

Analysts should tune queries using known-good devices, approved admin accounts, trusted software paths, expected parent processes, and internal allowlists where appropriate.

## Operational Safety

Do not blindly block, isolate, delete, or remediate based only on a single query result.

Recommended validation steps include:

* Confirm the device owner and business function.
* Review parent and child process relationships.
* Check command-line arguments.
* Review network connections.
* Compare activity against baseline behavior.
* Validate file hashes and signer information.
* Check whether the activity came from approved tooling.
* Preserve evidence before remediation when incident response is required.

## Naming and Organization

Recommended query naming format:

`MDE_<Category>_<Threat_or_Technique>_<Short_Description>.kql`

Example categories:

* `Initial_Access`
* `Execution`
* `Persistence`
* `Privilege_Escalation`
* `Defense_Evasion`
* `Credential_Access`
* `Discovery`
* `Lateral_Movement`
* `Command_And_Control`
* `Exfiltration`
* `Impact`
* `APT_IOC_Hunts`
* `Malware_Hunts`
* `Suspicious_Admin_Activity`

## Example Query Header Format

Each query should include a short header explaining what the query does, where the idea came from, and how it should be used.

```kql
// Query Name: MDE_Execution_Suspicious_PowerShell_Download_Cradle
// Purpose: Hunt for suspicious PowerShell command lines commonly associated with download cradle behavior.
// Source Type: Public reporting / TLP:CLEAR research
// Intended Use: Defensive cyber operations, SOC hunting, incident response
// Notes: Validate results against approved administration and software deployment activity.
```

## MITRE ATT&CK Mapping

Where possible, queries may include MITRE ATT&CK technique mappings. These mappings are included to help analysts understand the behavior being hunted and organize detections by adversary tactic.

MITRE mappings should be treated as a guide and may require adjustment based on the exact behavior, telemetry, and query logic.

## Contribution Guidelines

When adding or modifying queries:

* Use clear query names.
* Include a short description.
* Identify the primary MDE table or tables used.
* Include source context when applicable.
* Use public or TLP:CLEAR sources only.
* Avoid including private customer data.
* Avoid including sensitive internal information.
* Add comments for complex logic.
* Keep queries readable and easy to tune.
* Test queries before submitting.
* Include known false positive notes when possible.

## Prohibited Content

These queries will not include:

* Classified information
* Restricted information
* Proprietary threat intelligence without permission
* Private customer data
* Stolen data
* Live credentials
* Exploit instructions
* Malware source code
* Instructions for unauthorized access
* Non-public law enforcement or government information
* Any information that violates legal, contractual, or ethical requirements

## Legal and Authorization Notice

Use these queries only in systems and environments where you have explicit authorization to perform security monitoring, investigation, and threat hunting.

The user is responsible for ensuring that all use complies with applicable laws, contracts, policies, rules of engagement, privacy requirements, and organizational procedures.

## Repository Goal

The goal of this repository is simple:

Help defenders hunt smarter, move faster, and turn public threat reporting into practical Microsoft Defender for Endpoint visibility.

These queries are made by defenders, for defenders.
