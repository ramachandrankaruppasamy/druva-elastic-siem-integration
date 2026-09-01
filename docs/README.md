# Druva Integration for Elastic

## Overview

The Druva integration brings security, administrative, backup, recovery, data-access, unusual-data-activity, and cyber-resilience events from Druva Data Security Cloud into Elastic.

The parser normalizes Druva DCP Events API v2 and v3 JSON shapes into Elastic Common Schema (ECS) and Druva-specific fields while retaining the original `json.*` payload for investigation and troubleshooting.

The integration is designed to help security operations, incident response, threat hunting, data protection, recovery, and compliance teams investigate Druva activity alongside the rest of their security telemetry in Elastic.

## What this integration provides

### Security analytics

The package includes normalized actor and target identity, resource context, operation metrics, configuration-change fields, security-control context, dashboards, and Elastic Security detection content.

The included security content can help identify suspicious or high-risk activity involving administrators, identities, protected resources, backup and recovery operations, data access, configuration changes, and cyber-resilience controls.

### Detection rules

The package includes 155 Elastic Security detection rules for Druva telemetry.

The rules provide coverage across areas such as:

- Administrator and identity activity
- Backup and recovery operations
- Cyber-recovery activity
- Ransomware and unusual data activity
- Data access and privileged activity
- Security configuration and control changes
- Compliance and audit activity
- Behavioral correlation and threat investigation
- Integration and data-quality monitoring
- Cyber-resilience detections

Detection rules should be reviewed and enabled based on the customer's environment, available Druva event families, and SOC operating model.

### Dashboards

The package includes nine prebuilt Kibana dashboards for Druva security and cyber-resilience investigation workflows.

These dashboards are intended to help analysts answer questions such as:

- What security-relevant Druva activity is occurring?
- Which administrators, users, or identities are involved?
- Which protected resources or workloads are affected?
- Has backup or recovery activity changed during an incident?
- Have security controls or configurations been modified?
- What data-access or unusual-data-activity signals are present?
- What is the sequence of Druva activity during an investigation?
- What audit evidence is available for compliance review?

### Data normalization

Druva event content is normalized into ECS fields where appropriate while Druva-specific context is retained for investigation, correlation, and detection.

The original `json.*` payload is retained so analysts can pivot back to source event attributes when required.

### Cyber-resilience context

Druva telemetry can provide security teams with context about protected data, backup activity, recovery operations, security controls, and other activity relevant to determining the impact of an incident on the data-protection and recovery environment.

## Data stream

All supported Druva events are stored in:

`logs-druva.event-*`

Use this data stream in Discover, dashboards, investigations, and Elastic Security detection rules when working with Druva telemetry.

## Getting started

1. Install the Druva integration package in Elastic.
2. Configure the supported Druva event ingestion path for your environment.
3. Send a Druva test event.
4. Verify that Druva events are present in `logs-druva.event-*`.
5. Review the included dashboards.
6. Review and enable the detection rules appropriate for your environment.

## Validation

After configuring ingestion, verify that:

- Events are arriving in `logs-druva.event-*`.
- Druva event timestamps fall within the expected search window.
- ECS and Druva-specific normalized fields are populated.
- The original `json.*` payload is available when expected.
- Dashboard visualizations return data for the selected time range.
- Detection rules have the fields and event types required by their queries.

## Troubleshooting

### Events are not appearing

Check the Druva event destination, the ingestion endpoint or collector used by your deployment, and the Elastic data stream. Confirm that incoming event timestamps are within the time range selected in Kibana.

### Dashboards show no data

Confirm that events exist in `logs-druva.event-*`, expand the dashboard time range, and verify that the fields used by the visualizations are present in the ingested events.

### Detection rules are not generating alerts

Confirm that the rule is enabled and that the required event types and normalized fields are present. Also verify the rule lookback window and any threshold, cardinality, or sequence requirements used by the rule.

### A normalized field is missing

Inspect the retained `json.*` payload to determine whether the corresponding value was present in the original Druva event and compare it with the normalized ECS and Druva-specific fields.
