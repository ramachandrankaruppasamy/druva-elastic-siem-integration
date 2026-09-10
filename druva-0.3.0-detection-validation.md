# Druva Elastic Detection Validation — v0.3.0

## Summary

- Total detection rules: **31**
- Query/KQL rules: **16**
- EQL rules: **6**
- ES|QL rules: **9**
- KQL Detection Engine preview: **16/16 PASS**
- EQL + ES|QL runtime execution: **15/15 PASS**
- Behavioral positive validation: **31/31 PASS**
- Behavioral near-match negative validation: **31/31 PASS**
- Critical ingest-pipeline simulations: **12/12 PASS**
- `elastic-package format`: **PASS**
- `elastic-package check`: **PASS**
- `elastic-package build`: **PASS**

## Detection Rule Ledger

| # | Detection rule | Type | Rule ID | Runtime | Positive | Negative | Status |
|---:|---|---|---|---|---|---|---|
| 1 | Druva - Recovery Verification Failed | query | `03ba3f97-a60f-5ea8-8340-a3d0e2ceb0d9` | PASS | PASS | PASS | **PASS** |
| 2 | Druva - Protected Workload Removed | query | `05279f4c-aee0-556c-b4b5-b163a65ab2aa` | PASS | PASS | PASS | **PASS** |
| 3 | Druva - Unusual Data Activity Followed by Quarantine | eql | `053b140a-7b13-52ae-ba24-50e23a09d3bf` | PASS | PASS | PASS | **PASS** |
| 4 | Druva - Administrator Impossible Travel | esql | `09eb31b6-30ff-598f-a17b-ba49884c6631` | PASS | PASS | PASS | **PASS** |
| 5 | Druva - Webhook Authentication Changed | esql | `0c750cd3-b09d-5d11-8697-cc5224c5ad38` | PASS | PASS | PASS | **PASS** |
| 6 | Druva - Backup Repository Deleted | query | `1425e5a3-b9a5-5e24-9839-c7690c1f63a2` | PASS | PASS | PASS | **PASS** |
| 7 | Druva - Security Setting Disabled | esql | `14b94398-cf66-5148-8058-115fc5ecac00` | PASS | PASS | PASS | **PASS** |
| 8 | Druva - Recovery Target Changed | query | `171a6381-b684-50f9-9fce-aae841b28a56` | PASS | PASS | PASS | **PASS** |
| 9 | Druva - Mass Backup Failures | esql | `1aea63f1-20e2-5e21-8b86-629ec4d16b16` | PASS | PASS | PASS | **PASS** |
| 10 | Druva - Ransomware Alert Observed | query | `302df2ce-efa8-5c7c-ad5c-52ee5bd8825f` | PASS | PASS | PASS | **PASS** |
| 11 | Druva - Recovery Started After Backup Protection Disabled | eql | `332b01a5-7f94-53f8-bd0d-60197546530f` | PASS | PASS | PASS | **PASS** |
| 12 | Druva - Backup Data Deletion Attempt | query | `3ee7495f-f4bc-5f1d-afff-0d98b78c3181` | PASS | PASS | PASS | **PASS** |
| 13 | Druva - Backup Storage Target Changed | query | `46f4e6af-2e43-5393-af3c-c35741822164` | PASS | PASS | PASS | **PASS** |
| 14 | Druva - API Token Deleted | query | `4ac3a3ce-0bbc-550e-a02e-30301e76b8d9` | PASS | PASS | PASS | **PASS** |
| 15 | Druva - Malicious File Scan Configuration Activity | query | `4d6c0e6e-100e-5024-b616-a8535a1b924e` | PASS | PASS | PASS | **PASS** |
| 16 | Druva - Administrative Data Download | query | `50b9a940-11f9-576d-8287-00e3785b8f4c` | PASS | PASS | PASS | **PASS** |
| 17 | Druva - Privileged Role Assignment | esql | `51e65adf-132e-55d3-9568-774e2664d539` | PASS | PASS | PASS | **PASS** |
| 18 | Druva - Repeated Failed Administrator Logins | esql | `54841313-666c-5ccd-8a94-f490f74031e0` | PASS | PASS | PASS | **PASS** |
| 19 | Druva - Resource Removed From Quarantine | query | `66e07694-e4c0-5f63-bf73-3fe71f7759f6` | PASS | PASS | PASS | **PASS** |
| 20 | Druva - Recovery Started Immediately After UDA Alert | eql | `6f786ef7-5c7f-59f9-8c41-6d7efd24921e` | PASS | PASS | PASS | **PASS** |
| 21 | Druva - Successful Administrator Login After Multiple Failures | esql | `73fd99fc-de05-5572-8413-a9142f922338` | PASS | PASS | PASS | **PASS** |
| 22 | Druva - Short-Lived Administrator Account | eql | `88e8c044-fcff-5c2b-8ab9-da1e1ab6a865` | PASS | PASS | PASS | **PASS** |
| 23 | Druva - Backup Repository Permissions Changed | query | `a5d891e6-7411-5e9b-a5b9-1d0831358c60` | PASS | PASS | PASS | **PASS** |
| 24 | Druva - Backup Protection Disabled or Paused | query | `a8954dc8-0dab-57af-95fc-2b1f384e858d` | PASS | PASS | PASS | **PASS** |
| 25 | Druva - UDA Correlated With Backup Disablement | eql | `ba93b4ec-e65a-5a1c-8cc1-bad8180b9ce4` | PASS | PASS | PASS | **PASS** |
| 26 | Druva - Backup Retention Reduced or Removed | query | `be7a61d3-4e09-599e-9990-f931ddeb613a` | PASS | PASS | PASS | **PASS** |
| 27 | Druva - API Credential Modified | esql | `beee24cc-f03f-569f-86b1-cc3f4b73522d` | PASS | PASS | PASS | **PASS** |
| 28 | Druva - UDA Correlated With Backup Failure | eql | `ec1f0c22-3bcd-565a-8f45-a8890fc81465` | PASS | PASS | PASS | **PASS** |
| 29 | Druva - Administrator Self Privilege Escalation | esql | `ef1b31a6-65d8-561f-88a0-38a5c36d1101` | PASS | PASS | PASS | **PASS** |
| 30 | Druva - Unusual Data Activity Alert | query | `f6d4f3ba-7ba0-5ddb-a975-c31840c5c0ad` | PASS | PASS | PASS | **PASS** |
| 31 | Druva - Backup Encryption Disabled | query | `fbfe25b9-4d83-5f09-adf2-943d5bcc7e98` | PASS | PASS | PASS | **PASS** |

## Notes

- The 31 packaged detection rules were executed against Elastic 9.6 Serverless.
- Positive and near-match negative behavioral fixtures were evaluated in an isolated temporary validation index.
- The temporary validation index contained 0 documents at completion.
- Two initial behavioral fixture failures for administrator-role rules were caused by missing `druva.feature = "Admin Event"` in the test fixtures; the packaged rules did not require modification.
- No production Druva validation data was modified by the behavioral test harness.
- Local Docker-based `elastic-package test pipeline` was unavailable because Docker is not installed/available in the local test environment. Relevant parser behavior was validated using the installed Elasticsearch ingest pipeline `_simulate` API.
- This artifact is for Druva/internal and Elastic partner review. It is not approved for public/upstream publication.

