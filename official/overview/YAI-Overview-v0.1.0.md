Document ID: YAI-OVERVIEW
Title: YAI Overview
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

## One-liner
YAI is runtime governance infrastructure that converts autonomous AI execution into enforced policy with audit-grade evidence.

## What problem YAI solves
- Production AI is blocked by governance risk (security, compliance, change control)
- Monitoring is not enforcement; post-facto logs are not proof
- Teams lack a deterministic runtime grammar for decision → enforcement → evidence

## What YAI is (and is not)
- YAI enforces at runtime (fail-closed), emits verifiable evidence bundles
- YAI is not an LLM model; not an observability-only tool

## What is proven today (baseline)
- SC102 Wave 1 launch: deny/allow outcomes, pinned policy, verifiable manifest and index

## What comes next (near-term)
- TRL uplift via broader workflows and repeatable delivery (SC103)
- Hardening operator experience and attachment diagnostics

## References
- Evidence bundle: /evidence/waves/SC102-WAVE1-LAUNCH/
