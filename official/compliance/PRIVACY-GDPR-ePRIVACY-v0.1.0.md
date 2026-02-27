# PRIVACY — GDPR & ePrivacy (v0.1.0)

## Scope
This document defines YAI Ops privacy posture for pilots and evidence handling: data categories, processing activities, retention expectations, and evidence anchors. It supports customer privacy assessments; it does not provide legal advice.

## Audience
Customer legal/privacy stakeholders, security/compliance reviewers, delivery owners, and auditors reviewing how pilot artifacts (logs/evidence/waves) are handled.

## Non-goals
- This document is not a substitute for a customer-specific DPA, DPIA, or privacy notice.
- This document does not determine the customer’s lawful basis; it provides a structure to declare it in pilot instances.
- This document does not claim GDPR/ePrivacy compliance certification.

## Relationship to other baselines
- Applicability triggers are declared in: `/official/compliance/APPLICABILITY-MATRIX-v0.1.0.md`
- Evidence mapping is maintained in: `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`
- Internal compliance packs and schemas are incorporated by reference via yai-law (see: `/official/compliance/REFERENCES-v0.1.0.md`)

## Privacy posture (pilot-level)
YAI pilots are designed to:
- minimize the scope of processed data
- treat evidence artifacts as controlled outputs
- keep data residency and retention explicit and agreed in the pilot SOW
- support redaction or controlled access for sensitive artifacts

Default expectation:
- pilots should run in a controlled environment (staging / production-adjacent)
- evidence artifacts are reviewed before external sharing

## Data categories (typical)
Depending on the pilot workflow, YAI Ops artifacts may contain:

1) **Prompts / inputs**
- user or system inputs to the workflow, including instructions and parameters

2) **Outputs**
- model outputs, tool outputs, decision/outcome summaries

3) **Telemetry / logs / traces**
- operational logs, traces, metrics, verification outputs

4) **Identifiers / tokens**
- user identifiers, request IDs, workspace identifiers, API tokens (tokens must not be stored in evidence)

5) **Support artifacts**
- tickets, attachments, debugging bundles, incident notes (if used)

## Processing activities (pilot instance template)
Each pilot instance MUST document relevant activities. This table is a template; fill it per customer engagement.

| Activity | Data | Purpose | Lawful basis (customer-defined) | Retention | Controls | Evidence anchor |
|---|---|---|---|---|---|---|
| Pilot run execution | Inputs/outputs/logs | Execute governed workflow and produce evidence | TBD per customer | TBD | Least privilege; minimization; access control | Customer wave bundle (`/evidence/waves/<pilot>/`) |
| Verification | Verify outputs/logs | Validate wave integrity and outcomes | TBD | TBD | Controlled access; integrity checks | `/evidence/waves/<pilot>/verify/` |
| Reporting | Report + summary metrics | Communicate pilot results | TBD | TBD | Redaction where needed | `/evidence/reports/<pilot>/` |
| Support / debugging (optional) | logs/diagnostics | Resolve pilot-blocking issues | TBD | Short-lived | Sanitization/redaction | Support bundle path (if created) |

## Retention posture (pilot)
Retention is customer-specific and must be declared in the pilot SOW. Default posture for v0.1.0:
- evidence bundles (waves) are immutable artifacts; retention should be explicitly time-bounded unless the customer requires longer retention
- access should be limited to named roles (delivery owner, security/compliance reviewer)
- sensitive content should be excluded or redacted where possible

Internal baseline support:
- retention schemas and defaults may be taken from yai-law compliance packs (incorporated by reference).

## DPIA triggers (guidance)
A DPIA (or equivalent assessment) may be required depending on customer context, such as:
- high-risk sector workflows (critical services, regulated domains)
- systematic monitoring of individuals
- large-scale processing
- processing of special categories of data
- automated decision-making producing legal or similarly significant effects

Pilot instances should explicitly record whether DPIA is required and who is responsible.

## Controls (minimum set)
Minimum controls expected for pilots:

### Access control
- restrict access to evidence artifacts (principle of least privilege)
- separate environments/workspaces where applicable

### Data minimization
- collect only what is necessary to demonstrate deny/allow proofs and verification
- avoid storing sensitive tokens/credentials in evidence artifacts

### Encryption boundaries
- encrypt storage at rest where possible (customer-controlled storage preferred)
- encrypt in transit for evidence transfers (if any)

### Audit logging
- ensure evidence bundles include verification outputs and immutable indices
- record who produced/validated the wave and when (where applicable)

## Evidence anchors
- Privacy posture is operationalized by:
  - pilot SOW (`/collateral/sow/`)
  - pilot delivery spec (`/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`)
  - customer-grade wave bundle (`/evidence/waves/<pilot>/`)
- Baseline example wave (mechanism proof):
  - `/evidence/waves/SC102-WAVE1-LAUNCH/`