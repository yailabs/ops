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
This document defines what YAI is, the problem space it addresses, what is proven under the Evidence Baseline above, and a bounded near-term roadmap (non-binding unless promoted to evidence).

## Audience
Procurement, security/compliance, audit reviewers, and technical stakeholders needing a high-level system definition anchored to verifiable evidence.

## Non-goals
- This document does not provide legal advice. Legal posture is handled via the OFFICIAL legal pack and yai-law (incorporation by reference).
- This document does not claim general model safety guarantees. It describes runtime controls and evidence mechanics.
- Roadmap items are not “proven” unless explicitly linked to evidence waves.

## One-liner
YAI is runtime governance infrastructure that converts autonomous AI execution into enforced policy with audit-grade evidence.

## Problem statement (operational)
Production deployment of agentic/LLM-based systems is blocked by:
- missing runtime authority and policy enforcement over side effects (tool calls, egress, writes)
- weak reproducibility (configuration/params drift; no locked baselines)
- fragmented logs without chain-of-custody (post-facto observability ≠ proof)
- insufficient release-grade evidence for procurement and audit reviews

## What YAI is
YAI is a runtime-centric control plane that:
- evaluates authority and policy before effects occur (fail-closed)
- produces structured decision/outcome artifacts
- packages execution evidence into verifiable wave bundles (manifest/index/verify)

YAI is not:
- an LLM model
- an observability-only solution
- a “prompt framework” that relies on best-effort compliance

## Core concepts (canonical)
Canonical definitions are maintained in `/official/_glossary/TERMS-v0.1.0.md`. This overview uses the following primitives:
- Identity, Authority, Policy, Baseline, Decision, Outcome, Effect, Evidence, Run, Wave, Verification

## What is proven today (Evidence Baseline)
Under the Evidence Baseline declared in this document, the repository provides:
- an immutable evidence bundle (wave) with a pinned baseline and verification outputs
- deny/allow outcomes governed by the baseline policy (enforcement is fail-closed)
- verifiable indexing of evidence artifacts via manifest + index + verification procedure

Evidence entrypoint:
- `/evidence/waves/SC102-WAVE1-LAUNCH/`

## Proven claims (bounded)
The claims below are “proven” only in the context of this Evidence Baseline.

| Claim ID | Claim | Evidence anchor |
|---|---|---|
| YAI-CLM-OV-0001 | Evidence is shipped as immutable wave bundles with manifest/index and verification outputs. | /evidence/waves/SC102-WAVE1-LAUNCH/ (MANIFEST.json, INDEX.md, verify/) |
| YAI-CLM-OV-0002 | Enforcement produces deny/allow outcomes under a pinned policy/baseline (fail-closed). | /evidence/waves/SC102-WAVE1-LAUNCH/ (POLICY/, RUNS/, verify/) |

## Near-term roadmap (non-binding, not proven)
Roadmap items are goals; they become “proven” only when promoted into waves and referenced baselines.

- Operator experience hardening (CLI ergonomics, diagnostics, reproducible runbooks)
- Expanded workflows and qualification targets (SC103+)
- Data plane foundations (storage backends, retention/lineage anchors, queryability for audit/debug)
- Knowledge plane foundations (governed state updates; evidence-backed memory writes)

## Compliance posture (how evidence maps to requirements)
This repo maintains a compliance spine with explicit mappings from requirements to artifacts and evidence anchors:
- AI Act: `/official/compliance/AI-ACT-CROSSWALK-v0.1.0.md`
- Privacy: `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`
- Security & supply chain: `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`
- Evidence mapping table: `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`

## References
- Evidence bundle: `/evidence/waves/SC102-WAVE1-LAUNCH/`
- Canonical glossary: `/official/_glossary/TERMS-v0.1.0.md`
- Compliance spine: `/official/compliance/`