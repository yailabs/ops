# CONFORMITY & EVIDENCE MAP (v0.1.0)

## Scope
This is the canonical “single table” mapping from requirements to controls, repository artifacts, and concrete evidence anchors (waves/runs). It exists to make OFFICIAL claims auditable and to prevent narrative-only compliance posture.

## Audience
Security/compliance, audit reviewers, procurement stakeholders, and engineering leads.

## Rules
1) Each row must be evidence-backed or explicitly marked as planned.
2) Evidence pointers must reference immutable wave bundles whenever possible.
3) “Source” may be a regulation, standard, framework, or internal baseline (law).
4) This map does not certify compliance; it maps requirements to controls and evidence artifacts.

## Evidence Baseline (current)
Primary baseline for v0.1.0:
- Wave alias: `SC102-WAVE1-LAUNCH`
- Wave path: `/evidence/waves/SC102-WAVE1-LAUNCH/`

## Table
| Requirement ID | Source | Control / Process | Repo artifact(s) | Evidence pointer (wave/run) | Status |
|---|---|---|---|---|---|
| YAI-REQ-EVID-0001 | Internal (YAI Ops) | Evidence release unit is a wave: manifest + index + verify outputs | `/evidence/waves/*/MANIFEST.json`, `/evidence/waves/*/INDEX.md`, `/evidence/waves/*/verify/` | `/evidence/waves/SC102-WAVE1-LAUNCH/` | proven |
| YAI-REQ-EVID-0002 | Internal (YAI Ops) | Append-only evidence: waves are immutable; fixes create new waves | `GOVERNANCE.md`, `PUBLISHING-RULES.md`, `/evidence/waves/` | `/evidence/waves/SC102-WAVE1-LAUNCH/` + repository policy | proven |
| YAI-REQ-BASE-0001 | ISO/IEC 42001 (posture) | Baseline pinning: OFFICIAL claims must carry wave id + hashes + pins | `/official/_templates/FRONT-MATTER.md`, OFFICIAL docs baseline blocks | `/official/overview/YAI-Overview-v0.1.0.md` + `/evidence/waves/SC102-WAVE1-LAUNCH/` | proven |
| YAI-REQ-TRACE-0001 | NIST AI RMF (GOVERN) | Traceability for key claims: claim → evidence anchor | `/official/overview/`, `/official/assurance/`, `/official/tech-dossier/` | claim tables referencing SC102 wave | proven |
| YAI-REQ-ENF-0001 | Internal (YAI runtime posture) | Fail-closed enforcement: deny forbidden effects under policy/baseline | `/official/assurance/YAI-Assurance-Statement-v0.1.0.md`, wave policy artifacts | `/evidence/waves/SC102-WAVE1-LAUNCH/` (POLICY/, RUNS/, verify/) | proven |
| YAI-REQ-ENF-0002 | Internal (YAI runtime posture) | Explicit outcomes with reason codes (allow/deny/fail) as part of evidence | OFFICIAL: assurance/tech dossier; Evidence: runs/logs as captured | `/evidence/waves/SC102-WAVE1-LAUNCH/` (RUNS/ + verify outputs) | partial |
| YAI-REQ-DEL-0001 | ISO/IEC 42001 (operations) | Repeatable pilot delivery playbook with acceptance criteria and change control | `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`, `/collateral/sow/` | pilot instance wave (future) | planned |
| YAI-REQ-ACT-0001 | EU AI Act (logging/traceability posture) | Maintain audit-grade evidence artifacts for operated workflows (bounded) | `/evidence/waves/`, `/evidence/reports/`, `/official/assurance/` | `/evidence/waves/SC102-WAVE1-LAUNCH/` (bounded to baseline scenario) | partial |
| YAI-REQ-PRIV-0001 | GDPR (posture) | Declare data categories, purposes, retention, and access boundaries for pilot artifacts | `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`, law compliance packs | pilot instance (future) | planned |
| YAI-REQ-SEC-0001 | ISO 27001/27002 (posture) | Security baseline posture: least privilege, controlled effects, evidence retention access | `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`, `/official/assurance/` | `/evidence/waves/SC102-WAVE1-LAUNCH/` (bounded) | partial |
| YAI-REQ-SUP-0001 | NIST SSDF + SLSA (posture) | Release hygiene: pinned refs, reproducible verification, provenance expectations | `PUBLISHING-RULES.md`, verify outputs, pins referenced in OFFICIAL | SC102 wave baseline pins + verify outputs | partial |

## Notes on status
- **proven**: directly evidenced in an immutable wave and referenced in OFFICIAL.
- **partial**: concept is present and partially evidenced, but requires broader instrumentation or pilot instance evidence.
- **planned**: defined posture/process exists, but evidence will be produced during a pilot instance wave.

## Next actions (to move partial/planned → proven)
1) Promote a customer pilot instance into a dedicated wave (customer-grade wave).
2) Add run-level evidence indexes (machine-readable) where appropriate.
3) Expand instrumentation for selected KPIs (bytes, connections, effect counts) where needed for customer environments.