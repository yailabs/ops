Document ID: YAI-TECHDOSSIER
Title: YAI Technology Dossier
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
- Evidence map: /official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md

---

## Scope
This dossier describes YAI’s runtime architecture, canonical primitives, enforcement model, and evidence model. All “proven” statements are bounded to the Evidence Baseline declared above.

## Audience
Technical stakeholders evaluating architecture, security/compliance stakeholders assessing operational controls, and engineering teams planning integration.

## Non-goals
- This dossier does not provide legal advice (see OFFICIAL legal pack and yai-law by incorporation).
- This dossier does not claim model-level guarantees (accuracy/safety) beyond runtime enforcement and evidence mechanics.
- Roadmap items are not “proven” unless promoted into evidence waves.

## 1) System definition
YAI is a runtime-centric governance stack for intelligent systems. It provides:
- **Authority-first execution**: effects occur only under explicit identity/authority and policy (fail-closed)
- **Deterministic runtime grammar**: contract → decision → enforcement → outcome → evidence
- **Evidence as a release artifact**: execution proof is packaged into verifiable wave bundles (manifest/index/verify)

YAI is not:
- an LLM model
- an observability-only tool (logs without custody)
- a “prompt framework” that relies on best-effort compliance

## 2) Runtime planes (architecture overview)
YAI is organized into planes that separate responsibilities and enable controlled evolution:

- **Boot** — bring-up and environment verification
- **Root** — global control plane entrypoint; orchestration and attachment boundaries
- **Kernel** — authority + lifecycle + workspace isolation; core state and invariants
- **Engine** — execution plane for effects and providers (network/storage/tool gates)
- **Mind** — governed cognition: proposes decisions and workflows, never bypasses enforcement

Key property: the Mind is a **proposer**, not an executor. Execution remains mediated by kernel/engine enforcement.

## 3) Canonical primitives (runtime grammar)
Canonical definitions are in `/official/_glossary/TERMS-v0.1.0.md`. This dossier uses the following primitives:

- **Identity / Authority** — who acts, and with which powers in a given context
- **Policy** — evaluable rules for allowing/denying effects (pre/post constraints)
- **Baseline** — pinned configuration/version/params used for reproducibility and audit
- **Contract** — normative definition of expected behavior and boundaries (incorporated by reference via yai-law)
- **Decision** — proposed action, evaluated under authority and policy
- **Outcome / ReasonCode** — explicit result for each decision (allow/deny/fail), with reason
- **Effect** — an external side effect (egress, write, provider call, artifact emission)
- **Evidence** — structured artifacts emitted as part of execution and verification
- **Run** — a reproducible execution instance (inputs + baseline + outputs)
- **Wave / Bundle** — immutable evidence release unit (manifest/index/verify)
- **Verification** — deterministic verification procedure and outputs

### Normative source of truth (contracts)
Normative definitions and contracts are maintained in **yai-law** and incorporated by reference into this repository via pinned commits (see Evidence Baseline pins above). This prevents “documentation drift” between claims and normative definitions.

## 4) Enforcement model (fail-closed effects)
YAI enforces runtime governance by treating effects as controlled operations:
- effects are evaluated **before** they happen
- missing or invalid authority → deny/fail (fail-closed)
- policy violations → deny/fail
- outcomes are recorded with reason codes
- evidence artifacts are emitted for audit and reproducibility

### Effect classes (typical)
- network egress (HTTP/API calls)
- storage writes (local, S3-like object stores)
- provider actions (GitHub/Jira/Slack, etc.)
- artifact emission (reports, indices, run outputs)

YAI’s enforcement is structured to make “what happened” reconstructible:
- **decision** (intent) is separated from **effect** (external action)
- **outcome** is explicit, not implied by log scraping

## 5) Evidence model (waves as verifiable releases)
YAI treats proof as a first-class release artifact. A wave bundle contains:
- `MANIFEST.json` — bundle metadata + references
- `INDEX.md` — human index for navigation and audit review
- `POLICY/` — policy/baseline material used for the run (when applicable)
- `RUNS/` or referenced run directories — run inputs/outputs
- `verify/` outputs — verification results
- `verify.sh` (when present) — verification procedure

### Chain-of-custody (binding rule)
Any claim in OFFICIAL is valid only if it can be traced to:
CLAIM → WAVE → RUN → POLICY/BASELINE → VERIFY OUTPUT → EVIDENCE FILES

## 6) Determinism and reproducibility (bounded)
YAI supports deterministic behavior **where declared** by baseline and verification rules.
- determinism is expressed as an invariant plus a verification procedure
- reproducibility depends on pinned baselines (code, policy, inputs) and execution environment constraints

This dossier does not claim global determinism across all environments; it claims bounded determinism per Evidence Baseline and declared verification constraints.

## 7) Workspace model and isolation
Workspaces provide controlled execution contexts:
- isolation of policy, baselines, identities, and evidence boundaries
- multi-tenant posture (logical separation as a first-class concern)
- auditability at workspace granularity (runs and evidence attributed to contexts)

This model enables:
- separation between pilots, customers, environments (dev/staging/prod)
- controlled promotion (a run/wave can be promoted as a release baseline)

## 8) Mind layer (governed cognition)
The Mind layer (when present) is responsible for:
- workflow orchestration (planning, routing, memory access)
- proposing decisions based on governed knowledge
- maintaining operational knowledge structures (graphs, indices) as governed state

Critical constraint:
- Mind outputs are **proposals**. Execution is always subject to authority/policy enforcement and evidence emission.

## 9) Integration posture (what a pilot looks like)
A pilot integrates YAI as a runtime gate around one real workflow:
- identify effects to control (egress/tool/write)
- define minimal identity/authority model
- define policy baseline (allowlists, constraints, retention posture)
- run the workflow in a controlled environment
- produce a **customer-grade wave** + report + runbook

Deliverables are measurable and verifiable, not narrative-only.

## 10) Defensibility (moat)
YAI’s defensibility is primarily architectural and operational:

1) **Authority-first runtime grammar**
A stable, explicit execution grammar that separates decision, enforcement, outcome, and evidence.

2) **Evidence integrity as a release unit**
Waves are immutable bundles with verification, enabling procurement/audit workflows to consume proofs.

3) **Qualification system at scale**
Domain packs, scenarios, gates, and trials create a repeatable methodology for proving capabilities across domains (not just demos).

4) **Contracts as pinned baseline**
Normative contract sources (yai-law) are pinned and incorporated by reference, reducing drift between implementation, documentation, and proof.

---

## Appendix A — Proven references (Evidence Baseline)
- Evidence bundle: `/evidence/waves/SC102-WAVE1-LAUNCH/`
- Verify outputs: `/evidence/waves/SC102-WAVE1-LAUNCH/verify/`
- Bundle artifacts: `MANIFEST.json`, `INDEX.md`, `POLICY/`, `RUNS/` (as applicable)

## Appendix B — Related OFFICIAL anchors
- Overview: `/official/overview/YAI-Overview-v0.1.0.md`
- Assurance: `/official/assurance/YAI-Assurance-Statement-v0.1.0.md`
- Pilot delivery: `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`
- Compliance spine: `/official/compliance/`