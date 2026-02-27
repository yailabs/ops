# EU AI ACT — CROSSWALK (v0.1.0)

## Scope
This document maps EU AI Act obligation areas (by operator role) to YAI repository artifacts and evidence anchors. It is a compliance-support mapping, not a legal opinion and not a certification statement.

## Audience
Legal/compliance, security/audit, procurement, and delivery owners evaluating how YAI artifacts support AI Act-aligned controls and evidence.

## Non-goals
- This is not legal advice and does not determine whether a system is “high-risk” or what legal obligations apply in a specific case.
- This does not replace customer policies, conformity assessment activities, or required legal documentation.
- This does not claim full AI Act compliance; it maps obligation areas to controls and evidence artifacts.

## Relationship to other compliance docs
- Applicability and triggers: `/official/compliance/APPLICABILITY-MATRIX-v0.1.0.md`
- Evidence mapping table: `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`
- Privacy posture: `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`
- Security posture: `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`
- References and internal baseline: `/official/compliance/REFERENCES-v0.1.0.md` (yai-law incorporation by reference)

## Operator role positioning (declare per pilot/deployment)
For each pilot instance, declare which party holds which role(s). Typical pilot posture:

- **Provider**: the party that develops/places the AI system on the market (often YAI Labs for the runtime stack, and/or the customer for a final integrated system).
- **Deployer**: the party that uses the system under its authority (often the customer).
- **Importer/Distributor**: only if the system is imported/distributed as a product through a third party.
- **Authorized representative**: only if required for specific placement contexts.

### Pilot instance role declaration (template)
- Provider: `<party>`
- Deployer: `<party>`
- Importer/Distributor: `<party or N/A>`
- Authorized representative: `<party or N/A>`

## Evidence baseline (current)
Baseline example wave for v0.1.0 proof-of-mechanism:
- Wave alias: `SC102-WAVE1-LAUNCH`
- Wave path: `/evidence/waves/SC102-WAVE1-LAUNCH/`

## Crosswalk table
Legend:
- **Repo artifact(s)**: where the control/process is defined or documented.
- **Evidence anchor**: where proof artifacts exist (waves/runs/reports).
- **Status**: proven / partial / planned (see evidence map).

| Obligation area (AI Act) | Role(s) typically impacted | Expected control (high level) | Repo artifact(s) | Evidence anchor | Status |
|---|---|---|---|---|---|
| Risk management system | Provider / Deployer | Risk identification, mitigation planning, controlled changes | `/official/assurance/`, `/official/delivery/`, `/catalog/scenarios/`, yai-law contracts/invariants | Customer pilot wave (future) + pilot report | planned |
| Data governance (where applicable) | Provider / Deployer | Define data categories, access, retention, lineage boundaries | `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`, yai-law compliance packs | Customer pilot wave (future) | planned |
| Technical documentation | Provider | Maintain technical dossier, system definition, bounded claims | `/official/tech-dossier/`, `/official/overview/`, `/official/_templates/` | OFFICIAL baseline blocks + SC102 wave references | partial |
| Logging & traceability | Provider / Deployer | Produce audit-grade logs/evidence for operated workflows | `/evidence/waves/`, `/evidence/reports/`, `/official/assurance/` | `/evidence/waves/SC102-WAVE1-LAUNCH/` (manifest/index/verify) | partial |
| Instructions for use / operational constraints | Provider | Declare scope, limits, environment assumptions, verification steps | `/official/overview/`, `/official/assurance/`, `/official/delivery/` | SC102 wave + verify pointers | partial |
| Human oversight (where applicable) | Deployer / Provider | Define oversight checkpoints and decision gates in delivery | `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md` | Customer pilot wave (future) + pilot report | planned |
| Accuracy / robustness / cybersecurity (bounded) | Provider / Deployer | Controlled effects, baseline pinning, security posture, supply-chain hygiene | `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`, `PUBLISHING-RULES.md` | SC102 wave baseline pins + verify outputs | partial |
| Post-market monitoring / incident handling (where applicable) | Provider | Define issue intake, update process, wave supersedence policy | `GOVERNANCE.md`, `PUBLISHING-RULES.md`, `/evidence/waves/` append-only policy | Evidence policy + future release waves | planned |

## Notes (how to mature this crosswalk)
To move “planned/partial” items to “proven”:
1) Execute a **customer pilot instance** and publish a customer-grade wave:
   - `/evidence/waves/<customer-pilot-wave>/` with manifest/index/verify outputs
2) Produce a pilot report that maps outcomes to controls and obligation areas:
   - `/evidence/reports/<pilot>/`
3) Update `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md` rows to point to the customer wave anchors.