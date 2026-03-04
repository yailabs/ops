# Governance

## Scope
This document defines governance rules for yai-ops content production, review, and publication.

## Cross-repo authority context

`yai-ops` operates inside the platform governance chain:

`yai-law` -> `yai-sdk` -> `yai-cli` -> `yai` -> `yai-ops`

Authority boundaries:
- Normative law authority: `yai-law`
- SDK/CLI interface authority: `yai-sdk`, `yai-cli`
- Runtime implementation authority: `yai`
- Operational evidence and publication packaging: `yai-ops`

`yai-ops` must not redefine normative contract semantics; it must evidence them.

## Repository layers (non-negotiable boundaries)
yai-ops is organized into three layers with different immutability and publication rules:

1) `official/` — OFFICIAL documents (release-only, versioned)
- Audience: procurement, legal, security/compliance, partners, auditors.
- Content: claims, posture, controls, deliverables; MUST reference evidence baselines.
- Mutability: editable before release; after release, changes occur via new versions/releases.

2) `evidence/` — EVIDENCE & proof system (append-only)
- Audience: auditors, security/compliance, engineering.
- Content: runs, manifests, indices, policies/baselines, verification outputs, reports.
- Mutability: append-only. Existing waves MUST NOT be rewritten.
  - Corrections produce a new run and/or a new wave, with new references.

3) `collateral/` — Field collateral (fast iteration)
- Audience: field, partners, design partners, internal sales engineering.
- Content: decks, demo scripts, pilot offer/SOW drafts, ROI models.
- Mutability: can iterate rapidly, but MUST remain aligned to evidence baselines for any claims.

## Claim policy (traceability)
- Any claim in `official/` or `collateral/` MUST include a traceable evidence baseline:
  - wave alias and wave_id
  - manifest hash (and policy hash; index hash if used)
  - references to specific runs where applicable
- Claims without evidence must be explicitly labeled as non-verified and treated as roadmap notes (avoid in OFFICIAL).

## Roles and responsibilities
Minimum governance roles (can be held by the same person in early-stage mode):
- Maintainer: approves structure changes and release creation.
- Evidence steward: ensures append-only rules, manifest/index/verify integrity.
- Docs steward: ensures OFFICIAL coherence, glossary consistency, and crosswalk completeness.

## Review requirements (by layer)
- `evidence/`:
  - verify outputs must be present for waves that are referenced by OFFICIAL
  - wave manifest and index must be consistent and reviewable
- `official/`:
  - must conform to `official/_templates/FRONT-MATTER.md`
  - must use canonical terms from `official/_glossary/TERMS-v0.1.0.md`
  - must map key claims to `official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`
- `collateral/`:
  - must reference the same evidence baselines as OFFICIAL when making factual claims

## Change policy
- Structural changes (new folders, new normative schemas, changes to verification conventions) require maintainer approval.
- Evidence corrections are additive (new wave/run), never destructive.

## Source of truth for the execution plan
`TRACKING-HARDENING.md` is the canonical execution plan and Definition of Done reference for hardening and repository completion.
