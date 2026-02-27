Document ID: YAI-LEGAL
Title: YAI Legal & Commercial Pack (Pilot)
Version: v0.1.0
Status: DRAFT
Owner: <name, role>
Approved by:
Date: 2026-02-26

Evidence Baseline:
- Wave alias: SC102-WAVE1-LAUNCH
- Wave ID: WAVE-1-2026-02-25-578371a
- Manifest sha256: 9bf3305d06edc5d91c8c7a373d1f9268cef8d97fa266e0aa0d5cd244dcd3f00a
- Index sha256: ae29266cd8f5bbd249bcb0d2cc6c078afc39e17eb7edcd14abce1e323e0638e4
- Policy hash: faf40d98fd52b94cbbc81ed6d9205dd7efa9875413f4624c51b14f14f8aa3270
- yai git sha: 578371ad7f6e82df576cb61f4009b09082f3b9fd
- yai-cli git sha: 72e487ee55de2efaa7de71374427421a923aa5ed
- yai-law/specs pin sha: 20abef1874e56e4c3493df5a42697779cba00381

Verification Pointer:
- Wave path: /evidence/waves/SC102-WAVE1-LAUNCH/
- Verify output path: /evidence/waves/SC102-WAVE1-LAUNCH/verify/
- Verification procedure: /evidence/waves/SC102-WAVE1-LAUNCH/verify.sh

Terminology:
- Canonical glossary: /official/_glossary/TERMS-v0.1.0.md

Compliance anchors:
- Applicability: /official/compliance/APPLICABILITY-MATRIX-v0.1.0.md
- Privacy posture: /official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md
- Security posture: /official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md

---

## Scope
This document provides a pilot-oriented legal and commercial posture for YAI engagements. It is designed to support procurement and contracting conversations by defining boundaries, deliverables, and reference templates.

## Audience
Procurement, legal counsel, security/compliance stakeholders, and customer delivery owners.

## Non-goals
- This document is not legal advice. Final contracting terms must be reviewed and agreed by the parties.
- This document does not replace a customer-specific DPA, security addendum, or other contractual instruments required by the customer.
- This document does not modify any existing license terms of the repositories; it describes how pilots are typically structured and what is expected.

## Included templates and pointers (canonical)
- Pilot offer: `/collateral/pilot-offer/`
- Pilot SOW template(s): `/collateral/sow/`
- Pilot delivery specification (technical): `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`

## Contract baseline (incorporation by reference)
YAI maintains normative contracts, definitions, and posture documents in **yai-law**. For pilot engagements:
- yai-law is incorporated by reference as the canonical contract baseline.
- pilot instances should pin the yai-law revision (commit sha) used during delivery.
- any deviations from the baseline must be explicit and written into the pilot SOW / change note.

This protects both parties by preventing drift between “what is described,” “what is executed,” and “what is proven.”

## Commercial structure (pilot)
### Pilot intent
A pilot is a fixed-scope engagement intended to produce:
- a governed workflow integration (bounded)
- a customer-grade evidence wave (manifest/index/verify)
- a pilot report and runbook
- a day-14 expand/stop decision based on evidence

### Scope boundaries (default)
Unless explicitly modified in the pilot SOW:
- **1 workflow** (production-relevant)
- **1 environment**
- **2 proofs** (deny + allow)
- **1 evidence wave** as the primary proof artifact
- no production rollouts beyond the declared environment
- no generalized compliance certification statements

### Timeline and responsibilities
- Delivery timeline and responsibilities are fixed in the pilot SOW.
- Customer responsibilities typically include:
  - providing access to the agreed environment
  - providing necessary credentials with least privilege
  - assigning a pilot owner and a security/compliance point of contact (as needed)

### Support model (pilot)
Default support posture (unless superseded by SOW):
- best-effort engineering support during the pilot period
- issue triage and fix prioritization for pilot-blocking defects
- no “always-on” SLA commitments under the pilot pack

### Fees and payment terms
Fees and payment terms are defined in the pilot offer and SOW. This OFFICIAL pack does not set pricing; it sets the delivery shape and boundaries.

## Intellectual property and licensing posture (pilot)
### OSS and open-core posture
YAI may use an open-core approach depending on repository licensing and distribution model. For pilots:
- the customer receives deliverables as defined in SOW (wave bundle, report, runbook, configuration guidance)
- code licensing follows the licenses of the respective repositories (no implied additional rights)

### Customer data and customer materials
Customer-provided data, credentials, and materials remain customer-owned.
Handling rules must be defined in the SOW and (if needed) a DPA/security addendum.

### Contributions
If the customer requests changes to open repositories:
- contributions follow repository governance and licensing
- proprietary customer details must not be committed to public repos
- sensitive details may be captured via redacted evidence artifacts or private channels

## Data handling and privacy posture (pilot)
### Data boundaries
Pilot data handling must be explicitly agreed:
- what data is processed (inputs/outputs/logs/telemetry)
- where data is stored (customer environment vs controlled storage)
- how long evidence artifacts are retained
- who can access evidence artifacts

Reference posture and templates:
- `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`
- yai-law compliance packs (incorporated by reference)

### Retention and access
- evidence artifacts (waves) are immutable release bundles.
- customer-specific waves may require redaction or controlled access if they contain sensitive content.
- access controls and retention timelines must be defined in SOW or security addendum.

### Optional instruments (as required)
Depending on customer context, the following may be required:
- DPA (Data Processing Agreement)
- security addendum (controls, incident handling, audit rights)
- NDA / confidentiality agreement
These are customer-specific and are not replaced by this pack.

## Security posture (pilot)
Baseline security posture for pilot engagements:
- least privilege credentials
- secrets stored in customer-approved secret management
- controlled egress / provider access boundaries for the pilot workflow
- audit logging / evidence capture aligned to the pilot scope

Reference:
- `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`

## Risk and limitation posture
- YAI provides governance and evidence mechanisms for declared effects and baselines.
- YAI does not guarantee that a customer system is secure or compliant by default.
- Pilot outputs are bounded to the declared environment, workflow, and evidence baseline.

## References
- Pilot offer: `/collateral/pilot-offer/`
- Pilot SOW template(s): `/collateral/sow/`
- Pilot delivery spec: `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`
- Evidence baseline: `/evidence/waves/SC102-WAVE1-LAUNCH/`
- Compliance spine: `/official/compliance/`