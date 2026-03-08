Document ID: YAI-DELIVERY
Title: YAI Pilot Delivery Specification
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
- cli git sha: 72e487ee55de2efaa7de71374427421a923aa5ed
- law/specs pin sha: 20abef1874e56e4c3493df5a42697779cba00381

Verification Pointer:
- Wave path: /evidence/waves/SC102-WAVE1-LAUNCH/
- Verify output path: /evidence/waves/SC102-WAVE1-LAUNCH/verify/
- Verification procedure: /evidence/waves/SC102-WAVE1-LAUNCH/verify.sh

Terminology:
- Canonical glossary: /official/_glossary/TERMS-v0.1.0.md

Compliance anchors:
- Applicability: /official/compliance/APPLICABILITY-MATRIX-v0.1.0.md
- Evidence map: /official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md
- Privacy posture: /official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md
- Security posture: /official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md

---

## Scope
This specification defines the standard delivery process for a YAI pilot (v0.1.0). The pilot is engineered to produce a **customer-grade evidence wave** with verifiable outcomes and explicit boundaries.

## Audience
Customer engineering stakeholders, security/compliance reviewers, and delivery owners responsible for pilot execution and acceptance.

## Non-goals
- This pilot does not attempt to productionize a full AI system. It validates controlled execution and evidence mechanics on a single workflow.
- This pilot does not certify regulatory compliance; it produces evidence artifacts and mappings to support customer assessments.
- This pilot does not expand scope beyond what is explicitly listed here without a written change in the pilot instance (SOW / change note).

## Pilot scope (fixed constraints)
The pilot is intentionally constrained to reduce risk and guarantee a verifiable outcome:

- **1 workflow** (production-relevant) selected jointly with the customer
- **1 environment** (staging or controlled production-adjacent environment)
- **2 proofs** executed under governance:
  - **Deny proof**: a forbidden effect is blocked (fail-closed)
  - **Allow proof**: an allowed effect succeeds only for the contracted target
- **1 customer-grade evidence wave** with manifest/index and verification outputs
- **Day-14 decision**: expand or stop (explicit go/no-go gate)

## Entry criteria (preflight requirements)
The pilot can start only when these are satisfied:

### Environment access
- Execution environment available (runner, VM, container host, or designated machine)
- Network constraints documented (allowlists, proxies, egress restrictions)
- Credentials/secrets management defined (vault/secrets store), with least privilege

### Stakeholders
- Customer pilot owner (technical)
- Customer security/compliance point of contact (if applicable)
- YAI delivery owner (maintainer)

### Target workflow definition
The workflow must be described as:
- inputs and triggers
- expected outputs
- intended external effects (egress/tool/write)
- acceptable failure modes and rollback posture (if any)

## Delivery phases
### Phase 0 — Scoping & control surface mapping (Day 0–2)
Outputs:
- selected workflow definition (one-pager)
- effect inventory: what must be controlled
- minimal identity/authority model
- baseline constraints (pins/versions, policy set)

### Phase 1 — Baseline integration (Day 2–6)
Outputs:
- workflow executed through YAI governance boundaries
- policy baseline configured for:
  - allowlist target (what is permitted)
  - denylist / default-deny posture (what is forbidden)
- runbook draft (how to execute and verify)

### Phase 2 — Proof runs (Day 6–10)
Outputs:
- deny proof run (expected deny)
- allow proof run (expected allow)
- evidence artifacts captured for both runs
- preliminary report draft with outcomes and reason codes

### Phase 3 — Evidence wave packaging & verification (Day 10–12)
Outputs:
- customer-grade wave created under `/evidence/waves/`
  - MANIFEST.json + INDEX.md + verify outputs (and verify procedure if applicable)
- verification executed and recorded (verify exits 0)
- documentation baselined (pins/hashes recorded)

### Phase 4 — Review & day-14 decision (Day 12–14)
Outputs:
- pilot review meeting
- final pilot report
- explicit go/no-go decision:
  - expand (additional workflows/environments/effects)
  - stop (with evidence-backed rationale)

## Deliverables
Minimum deliverables (v0.1.0):

1) **Governed workflow configuration**
- workflow is executed with explicit identity/authority/policy boundaries
- effects are controlled (deny/allow behavior provable)

2) **Customer-grade evidence wave**
- immutable wave bundle containing:
  - manifest
  - index
  - policy/baseline references (where applicable)
  - run artifacts (inputs/outputs)
  - verify outputs and pass/fail evidence

3) **Pilot report**
- bounded claims and results
- deny/allow outcomes with reason codes
- key metrics (as available)
- gaps and recommendations for scale-up

4) **Walkthrough / runbook**
- how to execute runs
- how to verify the wave
- how to interpret outputs and reason codes

## Acceptance criteria (Definition of Done)
A pilot is accepted when all criteria below are satisfied:

### Verification
- The governed **run(s)** complete with expected exit status for each proof case.
- The wave **verification** completes successfully:
  - `verify` exits **0**
  - verification outputs are stored and referenced in the wave

### Deny proof (fail-closed)
- A forbidden effect is attempted and is blocked:
  - **0 forbidden successes**
  - outcome is explicit (deny/fail) with reason code
  - evidence artifacts show the attempted effect and enforcement result

### Allow proof (contracted allow)
- The allowed effect succeeds only for the contracted target:
  - effect succeeds under the allowlist constraints
  - effect does not succeed outside the contracted target (if tested)
  - evidence artifacts show the successful allowed effect

### Evidence wave integrity
- Wave includes at minimum:
  - MANIFEST.json
  - INDEX.md
  - verify outputs
- OFFICIAL baseline block for the pilot instance includes:
  - wave id + hashes + pins
  - pointers to verify outputs

## Metrics (minimum recommended)
Metrics depend on instrumentation and workflow. Minimum recommended:
- number of deny outcomes (by reason code)
- number of allow outcomes
- attempted effects vs executed effects
- verification pass status and time-to-verify (if captured)

Optional (when instrumented):
- network: attempted connections, connections established, bytes transmitted
- storage: bytes written, object count, write destinations

## Security and privacy posture (pilot-level)
- Principle of least privilege for credentials and provider access.
- Secrets handled via environment-approved secret management.
- Data handling constraints declared up-front (see privacy posture doc).
- Logs/evidence artifacts must be reviewed for sensitive content before external sharing.

Reference:
- `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`
- `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`

## Pilot expansion criteria (what unlocks next step)
Expansion requires a new pilot instance note (SOW/change) and typically includes:
- additional workflows
- additional environments (staging → production)
- broader effect surface (more providers, more egress targets)
- stronger data-plane requirements (retention/lineage, storage backends)

## References
- Collateral offer: `/collateral/pilot-offer/`
- SOW template: `/collateral/sow/`
- Evidence baseline (mechanism proof): `/evidence/waves/SC102-WAVE1-LAUNCH/`
- Compliance spine: `/official/compliance/`