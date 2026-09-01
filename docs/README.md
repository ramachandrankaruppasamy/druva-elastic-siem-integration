# Druva Integration for Elastic

## Overview

The Druva integration brings security and cyber-resilience telemetry from Druva Data Security Cloud into Elastic Security.

Use Druva telemetry in Elastic to detect suspicious activity, investigate security incidents, monitor privileged and administrative activity, identify unusual data behavior, analyze changes to backup and recovery controls, and understand whether an incident may have affected protected data or recovery readiness.

The integration ingests Druva security, administrative, backup, recovery, data-access, unusual-data-activity, configuration, and audit events and normalizes them for use across Elastic Security.

Druva DCP Events API v2 and v3 event structures are normalized into Elastic Common Schema (ECS) and Druva-specific fields. The original `json.*` payload is retained to preserve source context for investigation and troubleshooting.

The integration includes:

- 155 Druva-focused Elastic Security detection rules
- 10 security detection packs
- 9 prebuilt Kibana dashboards
- ECS and Druva-specific event normalization
- Cyber-resilience and recovery context for security investigations
- Detection coverage for identity, ransomware, unusual data activity, backup and recovery, data access, configuration changes, compliance, and integration health

## Why integrate Druva with Elastic Security?

Traditional security telemetry can help determine how an attack started, which identities or endpoints were involved, and how an adversary moved through an environment.

Druva telemetry adds another dimension to the investigation: what happened to the protected data and recovery environment.

By analyzing Druva events alongside endpoint, identity, network, cloud, and other security telemetry in Elastic, analysts can investigate questions such as:

- Did suspicious activity affect protected workloads or backup operations?
- Was backup protection disabled, paused, or modified?
- Were retention or recovery-related controls changed?
- Did unusual data activity occur on protected resources?
- Were privileged Druva administrators involved?
- Was sensitive or protected data accessed or downloaded?
- Did recovery activity begin during or after suspicious activity?
- Were recovery operations successful?
- Were security integrations, webhooks, or API credentials modified?
- Is the recovery environment still behaving as expected during an incident?

This allows Druva to provide data-protection and recovery context as part of the broader security investigation in Elastic.

## Security analytics

Druva events are normalized so that analysts can investigate activity using both standard ECS fields and Druva-specific security context.

Normalized context includes, where available:

- Actor and administrator identity
- Target identity
- Source IP address
- Event action and outcome
- Druva feature and event type
- Protected resource and workload context
- Backup and recovery status
- Unusual Data Activity (UDA) context
- File activity and change counts
- Security and configuration changes
- Webhook and integration changes
- Administrative operations
- Recovery operations
- Audit information

The original Druva event payload remains available under `json.*` for deeper investigation.

## Detection content

The integration provides 155 Elastic Security detection rules organized into 10 Druva detection packs.

The packs are designed to provide security coverage across the identity, data-protection, cyber-recovery, and administrative control planes represented by Druva telemetry.

### Detection Pack 0 – Core Cyber Resilience

Provides cross-domain detections that help identify activity that may affect the security or recoverability of protected data.

Coverage includes suspicious administrative behavior, backup-policy changes, protection changes, recovery activity, and other events that can help analysts evaluate cyber-resilience posture during an incident.

### Detection Pack 1 – Administrator & Identity

Focuses on privileged access and Druva administrator activity.

Example coverage includes:

- Newly observed administrator logins
- Administrator logins from new IP addresses
- VPN or TOR administrator access
- Repeated failed authentication
- Suspicious successful authentication
- Dormant administrator reactivation
- Administrator creation and deletion
- Administrator role changes
- Privilege-related activity
- Webhook configuration activity performed by administrators

These detections help identify compromised credentials, privileged-account misuse, and unexpected administrative access.

### Detection Pack 2 – Backup Operations

Monitors changes and anomalies affecting backup operations and protection behavior.

Coverage includes:

- Backup failures
- Backup success-rate degradation
- Backup SLA violations
- Backup policy modifications
- Protection disablement or suspension
- Retention changes
- Repository changes
- Backup storage and permission changes
- Unusually long backup activity

These detections help analysts determine whether an incident is affecting the organization's ability to maintain protected copies of critical data.

### Detection Pack 3 – Cyber Recovery & Recovery Operations

Focuses on restore and recovery activity that may be security relevant.

Coverage includes:

- Recovery activity following unusual data activity
- Recovery initiated after suspicious administrative activity
- Recovery failures
- Recovery cancellation or suspension
- Recovery target changes
- Mass recovery activity
- Multiple recovery jobs
- Recovery of critical workloads

This pack helps security and recovery teams correlate incident activity with recovery operations.

### Detection Pack 4 – Ransomware & Unusual Data Activity

Focuses on Druva security signals that may indicate ransomware or destructive data activity.

Coverage includes:

- Unusual Data Activity alerts
- High-volume file encryption
- High-volume file deletion
- Combined encryption and deletion behavior
- UDA affecting critical resources
- Quarantine activity
- UDA correlated with backup failures
- UDA correlated with protection changes
- UDA followed by recovery activity

These detections provide data-layer context that can complement endpoint and identity security signals during ransomware investigations.

### Detection Pack 5 – Data Access & Insider Risk

Monitors potentially suspicious access to protected data.

Coverage includes:

- Administrative data downloads
- Privileged data access
- Data access from new sources
- Rare data-access behavior
- Large or multiple downloads
- Access to sensitive resources
- Access with missing actor information
- Data access following security or policy changes

This pack can help analysts investigate insider-risk scenarios, compromised privileged accounts, and unusual access to protected information.

### Detection Pack 6 – Security Configuration & Integrations

Monitors changes to security controls and integrations that may affect monitoring or protection.

Coverage includes:

- Security settings being disabled
- Webhook configuration changes
- Webhook destination or authentication changes
- API credential and token activity
- Scan configuration changes
- Integration configuration changes
- Security configuration activity outside expected hours

These detections can help identify attempts to weaken controls, redirect telemetry, or modify security integrations.

### Detection Pack 7 – Compliance & Audit

Provides visibility into security-relevant administrative and policy changes that may require audit or compliance review.

Coverage includes:

- Retention policy changes
- Legal hold configuration changes
- Privileged role assignments
- Compliance policy changes
- Audit configuration changes
- Administrative activity with incomplete attribution
- High-severity administrative audit events

The pack can support security investigations as well as audit and governance workflows.

### Detection Pack 8 – Behavioral Correlation & Threat Hunting

Correlates activity across Druva event families to identify patterns that may be more meaningful than individual events.

Coverage includes relationships between:

- Authentication and privileged activity
- Administrative and backup activity
- UDA and administrative activity
- Security events and recovery activity
- Data access and policy changes
- Failed and successful operations
- Multiple event families affecting the same protected resource

This pack is intended for higher-context detections and threat-hunting workflows.

### Detection Pack 9 – Connector, Parser & Data Quality

Monitors the health and completeness of Druva security telemetry in Elastic.

Coverage includes:

- Missing event identifiers
- Missing actors
- Missing event actions
- Missing timestamps
- Dataset mismatches
- Unknown event families
- Parsing failures
- Ingest pipeline errors
- Unexpected metadata

These detections help identify telemetry gaps that could otherwise reduce investigation or detection coverage.

> Detection rules should be reviewed and enabled based on the Druva features in use, the event families available in the customer's environment, and the organization's SOC operating model.

## Dashboards

The integration includes nine prebuilt Kibana dashboards designed around security investigation and cyber-resilience workflows rather than infrastructure monitoring alone.

Together, the dashboards help analysts move from broad security posture and activity into identity, data, protection, recovery, configuration, and audit context.

### Security Operations Overview

Provides a starting point for Druva security monitoring in Elastic.

Use this dashboard to identify significant Druva security activity, unusual events, affected resources, administrative actions, and other signals that may require investigation.

### Identity & Administrative Security

Focuses on administrator authentication, privileged activity, account lifecycle changes, and administrative actions.

Use this dashboard to investigate who performed an action, where administrative access originated, and whether privileged behavior appears unusual.

### Data Protection & Recovery Operations

Provides visibility into backup, protection, restore, and recovery activity.

Use this dashboard during an incident to understand whether backup operations are succeeding and whether recovery-related activity or configuration has changed.

### Insider & Privileged Access

Focuses on privileged access to protected data and potentially unusual administrative or download behavior.

Use this dashboard to investigate sensitive data access, privileged users, source addresses, and affected resources.

### Compliance & Audit

Provides an audit-oriented view of Druva administrative, configuration, policy, and security activity.

Use this dashboard to investigate changes that may affect retention, security controls, administrative privileges, or compliance posture.

### Cyber Incident & Recoverability

Connects security activity with backup and recovery context.

Use this dashboard during incident response to determine whether protected resources, backup operations, or recovery readiness may have been affected.

### Threat Investigation & Attack Timeline

Provides a timeline-oriented view of Druva activity during an investigation.

Use it to correlate administrative activity, unusual data activity, data access, backup events, and recovery actions to understand how activity progressed over time.

### Security Configuration & Control Changes

Focuses on changes to security-relevant configuration.

Use this dashboard to identify modifications to protection settings, policies, integrations, webhooks, security controls, and other configuration that may affect the security or recoverability of Druva-managed data.

### Compliance & Audit Investigation

Provides deeper investigation of administrative and audit events for governance, security review, and evidence collection.

Use this dashboard to identify who changed what, when the change occurred, which resources were affected, and what related activity occurred around the same time.

## Investigating a cyber incident with Druva and Elastic

Druva telemetry can complement other Elastic Security data sources throughout an investigation.

A typical investigation can follow this sequence:

1. Identify suspicious activity from endpoint, identity, cloud, network, or Druva detections.
2. Determine which users, administrators, workloads, and protected resources are involved.
3. Review Druva unusual-data-activity and protected-data signals.
4. Check whether backup protection, retention, policies, or security controls changed.
5. Determine whether backup operations continued successfully during the incident.
6. Review restore and recovery activity.
7. Investigate whether recovery attempts succeeded or failed.
8. Use Druva audit events to reconstruct administrative activity.
9. Determine whether the protected-data and recovery environment requires additional investigation before recovery.

## Data normalization

Druva DCP Events API v2 and v3 event structures are normalized into ECS fields where appropriate.

Druva-specific context is retained under the `druva.*` namespace.

The original source payload is retained under:

`json.*`

This allows analysts to use normalized fields for correlation and detection while retaining the source event for detailed investigation.

## Data stream

Supported Druva events are stored in:

`logs-druva.event-*`

Use this data stream with:

- Elastic Discover
- Kibana dashboards
- Elastic Security detection rules
- ES|QL investigations
- Threat-hunting workflows

## Getting started

1. Install the Druva integration package in Elastic.
2. Configure the supported Druva event ingestion path for your environment.
3. Configure Druva to send supported events to the Elastic ingestion endpoint.
4. Send a Druva test event.
5. Verify that events are present in `logs-druva.event-*`.
6. Confirm that normalized ECS and `druva.*` fields are populated.
7. Review the included dashboards.
8. Review and enable the detection packs appropriate for your environment.

## Validation

After configuring ingestion, verify that:

- Events are arriving in `logs-druva.event-*`.
- Druva event timestamps fall within the expected search window.
- ECS and Druva-specific normalized fields are populated.
- The original `json.*` payload is retained when expected.
- Dashboard visualizations return data for the selected time range.
- Detection rules have the event types and fields required by their queries.
- Threshold, cardinality, new-terms, and sequence rules have sufficient data history to evaluate correctly.

## Troubleshooting

### Events are not appearing

Check the Druva event destination, ingestion endpoint or collector, and Elastic data stream.

Confirm that incoming timestamps fall within the selected Kibana time range.

### Dashboards show no data

Confirm that events exist in `logs-druva.event-*`, expand the dashboard time range, and verify that the fields required by the visualizations are populated.

### Detection rules are not generating alerts

Confirm that the rule is enabled and that the required Druva event types and normalized fields are present.

For behavioral rules, also verify the rule lookback window and any threshold, cardinality, historical, new-terms, or sequence requirements.

### A normalized field is missing

Inspect the retained `json.*` payload to determine whether the corresponding value was present in the original Druva event and compare it with the normalized ECS and Druva-specific fields.
