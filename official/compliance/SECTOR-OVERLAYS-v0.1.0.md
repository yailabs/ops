# SECTOR OVERLAYS (v0.1.0)

## Scope
This document declares additional controls and evidence expectations that may be triggered by sector-specific requirements. It is a trigger-and-evidence guide, not a certification statement.

## Audience
Security/compliance, legal, procurement, and delivery owners determining whether overlay obligations apply to a pilot or deployment.

## Rules
1) Overlays are activated only when their trigger conditions are met (see `/official/compliance/APPLICABILITY-MATRIX-v0.1.0.md`).
2) When an overlay is activated, the pilot instance MUST record:
   - the trigger reason
   - the additional controls agreed
   - the evidence artifacts that will be produced
3) Overlays are supported by evidence and posture documents; they do not replace customer-specific policies and contractual instruments.

## NIS2 (Directive (EU) 2022/2555)
### Trigger (when to activate)
Activate this overlay when:
- the customer is an “essential” or “important” entity under NIS2 (or equivalent national transpositions), or
- the engagement falls into a critical supply-chain posture where NIS2-aligned expectations are contractually required.

### Control / process expectations (pilot-level)
- security governance and incident handling expectations are explicit for the pilot
- access control, least privilege, and logging posture are documented
- change control for the governed workflow is explicit (what can change during the pilot)

### Expected evidence (what to produce)
- pilot delivery documentation with scope boundaries and DoD:
  - `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`
- security posture mapping (baseline):
  - `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`
- immutable customer-grade wave bundle (pilot instance):
  - `/evidence/waves/<customer-pilot-wave>/` (manifest/index/verify)
- pilot report summarizing outcomes and deny/allow proofs:
  - `/evidence/reports/<pilot>/`

## DORA (Regulation (EU) 2022/2554)
### Trigger (when to activate)
Activate this overlay when:
- the customer is in the financial sector and the pilot touches ICT-supported functions, or
- the customer treats the engagement as an ICT third-party provider relationship under DORA expectations.

### Control / process expectations (pilot-level)
- operational resilience posture: explicit boundaries, recovery expectations, and failure modes
- logging and traceability of actions and outcomes (auditability)
- change control around baselines/pins for the pilot workflow

### Expected evidence (what to produce)
- pilot SOW and scope boundaries (including resilience expectations):
  - `/collateral/sow/`
- controlled execution evidence and verification:
  - `/evidence/waves/<customer-pilot-wave>/verify/`
- report with operational outcomes and (where instrumented) stability metrics:
  - `/evidence/reports/<pilot>/`
- documentation of baseline pinning and release hygiene:
  - `PUBLISHING-RULES.md` + OFFICIAL baseline blocks

## Data Act (Reg. (EU) 2023/2854) + Data Governance Act (Reg. (EU) 2022/868)
### Trigger (when to activate)
Activate this overlay when the pilot or deployment includes:
- regulated data sharing/access rights posture (Data Act), or
- data intermediation / data governance structures consistent with DGA contexts, or
- marketplace-like data access/usage arrangements requiring explicit governance.

### Control / process expectations (pilot-level)
- explicit declaration of data categories, purposes, retention, and access rules
- explicit policy boundaries for data movement and storage (where applicable)
- evidence artifacts reviewed for sensitive content and access-controlled

### Expected evidence (what to produce)
- privacy and data handling declarations:
  - `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`
  - pilot instance declarations in `/collateral/sow/`
- evidence wave with clear artifact inventory (what data is included):
  - `/evidence/waves/<customer-pilot-wave>/INDEX.md`
- retention and access rules (pilot instance):
  - SOW clauses + yai-law retention policy schema (incorporated by reference, if used)

## Pilot instance overlay declaration (template)
For each pilot instance, record:
- Activated overlays: NIS2 / DORA / Data Act+DGA
- Trigger rationale:
- Added controls:
- Evidence artifacts to be produced:
- Wave baseline:
  - alias, id, hashes, pins