# Druva Elastic Security Content

This document summarizes the security content included with the Druva integration for Elastic.

The integration normalizes supported Druva security, administrative, backup, recovery, data-access, unusual-data-activity, and cyber-resilience events into Elastic Common Schema (ECS) and Druva-specific fields.

The package includes:

- One Druva event dataset: `druva.event`
- 31 Elastic Security detection rules
- Nine Kibana dashboards
- ECS and Druva-specific field mappings
- An ingest pipeline for supported Druva event structures
- Pipeline test coverage for representative Druva events

## Event normalization

Supported Druva events are normalized into:

`logs-druva.event-*`

The ingest pipeline maps common event attributes to ECS fields and maps Druva-specific security, data-protection, recovery, and operational context under the `druva.*` namespace.

Normalization includes, where available:

- Event identifiers, actions, categories, types, outcomes, and severity
- User, administrator, service, API, and target identity context
- Source IP information
- Protected resource and workload context
- Unusual Data Activity (UDA)
- File activity associated with UDA
- Backup and protection activity
- Restore, recovery, rollback, and data-access operations
- Security-control and configuration changes
- Webhook configuration activity
- Druva SIEM identity, publisher, topic, and schema context

Field availability varies by Druva event family and the attributes present in the source event.

## Detection rules

The package includes 31 Elastic Security detection rules.

Detection coverage includes:

- Administrator and identity activity
- Authentication activity
- Privileged access and privilege changes
- API credential activity
- Security-control changes
- Webhook authentication changes
- Unusual Data Activity
- Ransomware-related activity
- Backup failures and protection changes
- Backup repository and retention changes
- Recovery and rollback activity
- Data-access activity
- Quarantine activity
- Correlated security and recovery behavior

The packaged detection rules are:

1. Druva - Recovery Verification Failed
2. Druva - Protected Workload Removed
3. Druva - Unusual Data Activity Followed by Quarantine
4. Druva - Administrator Impossible Travel
5. Druva - Webhook Authentication Changed
6. Druva - Backup Repository Deleted
7. Druva - Security Setting Disabled
8. Druva - Recovery Target Changed
9. Druva - Mass Backup Failures
10. Druva - Ransomware Alert Observed
11. Druva - Recovery Started After Backup Protection Disabled
12. Druva - Backup Data Deletion Attempt
13. Druva - Backup Storage Target Changed
14. Druva - API Token Deleted
15. Druva - Malicious File Scan Configuration Activity
16. Druva - Administrative Data Download
17. Druva - Privileged Role Assignment
18. Druva - Repeated Failed Administrator Logins
19. Druva - Resource Removed From Quarantine
20. Druva - Recovery Started Immediately After UDA Alert
21. Druva - Successful Administrator Login After Multiple Failures
22. Druva - Short-Lived Administrator Account
23. Druva - Backup Repository Permissions Changed
24. Druva - Backup Protection Disabled or Paused
25. Druva - UDA Correlated With Backup Disablement
26. Druva - Backup Retention Reduced or Removed
27. Druva - API Credential Modified
28. Druva - UDA Correlated With Backup Failure
29. Druva - Administrator Self Privilege Escalation
30. Druva - Unusual Data Activity Alert
31. Druva - Backup Encryption Disabled

Detection rules should be reviewed and enabled based on the Druva event families available in the environment, expected administrative behavior, and the organization's SOC operating model.

Some detections depend on thresholds, correlations, or event sequences and therefore require multiple related events rather than a single Druva event.

## Dashboards

The package includes nine Kibana dashboards:

1. Druva - Security Operations Overview
2. Druva - Detection Coverage & SOC Health
3. Druva - Identity & Administrative Security
4. Druva - Insider & Privileged Access
5. Druva - Data Protection & Recovery Operations
6. Druva - Threat Investigation & Attack Timeline
7. Druva - Security Configuration & Control Changes
8. Druva - Cyber Incident & Recoverability
9. Druva - Compliance & Audit

The dashboards provide views into security activity, identity and administrative behavior, data-protection and recovery operations, security-control changes, threat-investigation timelines, cyber recoverability, and compliance activity.

Dashboard results depend on the Druva event families available in the environment, activity that has occurred, and the selected Kibana time range.

## Pipeline test coverage

Pipeline test fixtures are included for representative Druva events.

The current test corpus contains:

- 85 events in the documented event corpus
- 29 representative native Druva events
- 114 total test events

The fixtures cover multiple Druva event families, including administrative activity, authentication, API activity, backup and recovery, data access, Unusual Data Activity, ransomware recovery, alerts and notifications, webhook configuration, quarantine activity, and other security-relevant events.

Package validation can be run with:

```shell
elastic-package format
elastic-package check
```
