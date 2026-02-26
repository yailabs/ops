# APPLICABILITY MATRIX (v0.1.0)

## Purpose
Declare what is CORE vs what is OVERLAY and which triggers enable overlays.

## Matrix
| Item | Type | Trigger | Applies when | Evidence anchor |
|---|---|---|---|---|
| EU AI Act | CORE | Always | EU placement/use context | official/compliance/AI-ACT-CROSSWALK |
| GDPR | CORE | Personal data | Logs/prompts/telemetry/support include personal data | official/compliance/PRIVACY-GDPR-ePRIVACY |
| ePrivacy | CORE* | Communications identifiers | Applicable communications context | official/compliance/PRIVACY-GDPR-ePRIVACY |
| ISO/IEC 42001 | CORE | Always (target posture) | Management system posture | official/compliance/CONFORMITY-EVIDENCE-MAP |
| ISO/IEC 23894 | CORE | Always (risk posture) | Risk mgmt posture | official/compliance/CONFORMITY-EVIDENCE-MAP |
| NIST AI RMF | CORE | Always (mapping) | Customer/audit mapping | official/compliance/CONFORMITY-EVIDENCE-MAP |
| ISO 27001/27002 | CORE | Always (security baseline) | Procurement baseline | official/compliance/SECURITY-AND-SUPPLY-CHAIN |
| NIST SSDF + SLSA | CORE | Always (supply chain) | CI/CD and releases | official/compliance/SECURITY-AND-SUPPLY-CHAIN |
| CRA | OVERLAY | product distribution | product w/ digital elements in scope | official/compliance/SECURITY-AND-SUPPLY-CHAIN |
| NIS2 | OVERLAY | sector | essential/important entity supply chain | official/compliance/SECTOR-OVERLAYS |
| DORA | OVERLAY | finance | financial sector ICT provider | official/compliance/SECTOR-OVERLAYS |
| Data Act + DGA | OVERLAY | data sharing | sharing/intermediation use cases | official/compliance/SECTOR-OVERLAYS |
