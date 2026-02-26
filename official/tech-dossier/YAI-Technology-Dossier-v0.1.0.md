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

---

## 1. Architecture overview
- Runtime planes: Boot / Root / Kernel / Engine / Mind
- Deterministic runtime grammar: contract → decision → enforcement → evidence

## 2. Canonical primitives and contracts
- Primitive registry, policy baselines, reason codes, effects, evidence model
- Note: normative source of truth is yai-law (pinned by sha)

## 3. Enforcement and evidence loop
- Fail-closed behavior for non-contracted effects
- Evidence bundle: manifest, index, policy pin, runs, verification

## 4. Mind layer (governed cognition)
- Durable operational knowledge and workflow orchestration
- All actions remain governed: decisions produce enforcement and evidence

## 5. Moat / defensibility
- Domain-pack abstraction + wave qualification system + verifiable evidence integrity

## Appendix: Proof references
- Evidence bundle: /evidence/waves/SC102-WAVE1-LAUNCH/
