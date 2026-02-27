# SECURITY & SUPPLY CHAIN (v0.1.0)

## Scope
This document defines the baseline security posture for YAI Ops pilots and evidence handling, and maps software supply-chain integrity expectations to repository artifacts. It also declares the CRA overlay trigger posture.

## Audience
Security engineering, compliance/audit reviewers, procurement stakeholders, and delivery owners.

## Non-goals
- This document is not a security certification or guarantee.
- This document does not replace customer security policies, security addenda, or vulnerability management programs.
- This document describes posture and evidence anchors; customer-specific controls are declared in pilot instances (SOW/delivery notes).

## Relationship to other baselines
- Applicability triggers: `/official/compliance/APPLICABILITY-MATRIX-v0.1.0.md`
- Evidence mapping: `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`
- Privacy posture: `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`

## Security baseline (pilot-level posture)
The pilot security posture is built on the following baseline principles (aligned to ISO/IEC 27001/27002 style control families):

1) **Least privilege**
- credentials and tokens are provisioned with minimum required scopes
- access to evidence artifacts is role-restricted

2) **Controlled effects**
- external effects (egress/tool/write) are explicitly governed by policy where integrated
- deny-by-default is preferred for non-contracted targets

3) **Secrets handling**
- secrets are stored via customer-approved secret management (GitHub Secrets, vault, KMS, etc.)
- secrets must not be committed into repositories or emitted into evidence artifacts
- evidence artifacts must be reviewed for leakage risk when shared externally

4) **Logging and monitoring**
- evidence artifacts (waves) provide an audit-grade index of what occurred
- optional telemetry (OTEL) is used where required for detailed KPIs (connections, bytes, traces)

5) **Change control (baseline pinning)**
- OFFICIAL documents and pilot instances pin baselines (code, policy hashes)
- changes during the pilot require explicit update and re-verification

## Evidence anchors (baseline)
- OFFICIAL baseline blocks: `/official/_templates/FRONT-MATTER.md`
- Release rules: `PUBLISHING-RULES.md`
- Evidence waves: `/evidence/waves/`
- Baseline example wave: `/evidence/waves/SC102-WAVE1-LAUNCH/`

## Supply chain integrity posture
Supply chain posture is expressed via two layers:
- development and build practices (SSDF-aligned)
- provenance expectations for released artifacts (SLSA-aligned)

### NIST SSDF (SP 800-218) — posture mapping (high level)
The following SSDF areas are supported by YAI Ops artifacts and process rules:

- **Prepare the organization (PO)**
  - governance rules for release and evidence production:
    - `GOVERNANCE.md`
    - `PUBLISHING-RULES.md`

- **Protect the software (PS)**
  - pinning and baseline hygiene:
    - OFFICIAL Evidence Baseline blocks
    - wave manifests/hashes where applicable

- **Produce well-secured software (PW)**
  - repeatable verification gates and checks (where integrated via yai-infra and repo tooling)
  - controlled publishing rules and verification outputs

- **Respond to vulnerabilities (RV)**
  - vulnerability intake and response posture (see below)

This posture is intended to be auditable via repository artifacts and evidence outputs rather than policy text alone.

### SLSA — provenance expectations (high level)
For releases and waves, provenance expectations are:
- pinned refs for critical dependencies (code and policy baselines)
- reproducible verification procedures (verify scripts / outputs)
- immutable evidence bundles (waves) as release artifacts

Where feasible, releases should:
- tag and publish immutable baselines
- store verification outputs alongside the artifact (wave verify/)

## Vulnerability intake and handling (posture)
YAI follows a standard vulnerability-handling posture:
- provide a security contact channel (repository SECURITY.md where applicable)
- triage reported vulnerabilities
- publish fixes via versioned releases
- issue advisories where appropriate

Pilot customers may require additional vulnerability clauses via security addendum; those are negotiated per pilot.

## CRA overlay (Reg. (EU) 2024/2847) — when applicable
### Trigger
Activate CRA overlay when:
- YAI is distributed as a product/software with digital elements in CRA scope, or
- the customer contractually requires CRA-aligned posture for software delivered/operated.

### Overlay expectations (evidence-oriented)
When CRA overlay is activated, pilot instance documentation should include:
- vulnerability handling posture and timelines (as agreed)
- change control and release hygiene for delivered artifacts
- traceable evidence of verification for the delivered bundle (wave/proof pack)

### Expected evidence
- security posture doc (this file) + pilot SOW clauses
- wave bundle(s) with manifest/index/verify:
  - `/evidence/waves/<customer-pilot-wave>/`
- release/publishing rules and baseline pinning:
  - `PUBLISHING-RULES.md`
  - OFFICIAL baseline blocks in delivered documents

## Pilot instance security declaration (template)
For each pilot instance, record:
- environment and access model (who can run, where logs go)
- secrets management approach
- controlled effects list (egress/tool/write)
- activated overlays (CRA/NIS2/DORA) and triggers
- evidence wave baseline (alias/id/hashes/pins)