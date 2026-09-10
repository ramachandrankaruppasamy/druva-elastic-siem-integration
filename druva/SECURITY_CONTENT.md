# Druva Elastic Security content

## Parser changes
- `json.details.eventID` is used as `event.id` when present.
- `json.globalID` is retained as `druva.customer.id`; it is not an event identifier.
- Actor and protected-user identities cover v2/v3 variants including `initiator*`, `email`, `admin*`, and `inSyncUser*`.
- Resource normalization covers `resource*`, `inSyncDataSource*`, VMware/job variants.
- Backup/restore/download metrics are extracted from deterministic `eventDetails` key/value text.
- `oldState`/`newState` differences produce `druva.change.fields` and `druva.change.count`.
- Deterministic security-control reductions are derived for MFA, administrator geofencing, and curated IOC scan settings.

## Detection rules
`security_rules/druva_detection_rules.ndjson` contains 74 disabled-by-default rules. Import them through Elastic Security > Detection rules (SIEM) > Import rules. Review/tune before enabling.

## Dashboards
The `kibana/dashboard` folder contains the prior dashboard API export updated for the Druva data stream and normalized common fields. Because the supplied export came from a deprecated saved-objects listing endpoint rather than a portable NDJSON export, validate/import these in Kibana before treating them as production package assets.

## Validation
Run `elastic-package format`, `elastic-package build`, and `elastic-package check` in your local package environment. Replay representative Druva events and compare normalized-field coverage before/after.
