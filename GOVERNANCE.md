# Governance

## Scope
This document defines governance rules for `ops` content production, review, and publication.

## Cross-repo authority context

`ops` operates inside the platform governance chain:

`law` -> `sdk` -> `cli` -> `yai` -> `ops`

Authority boundaries:
- Normative law authority: `law`
- SDK/CLI interface authority: `sdk`, `cli`
- Runtime implementation authority: `yai`
- Operational evidence and publication packaging: `ops`

`ops` must not redefine normative contract semantics; it must evidence them.

## Repository layers (non-negotiable boundaries)

1) `official/` — OFFICIAL documents (release-only, versioned)
- Audience: procurement, legal, security/compliance, partners, auditors.
- Content: claims, posture, controls, deliverables; MUST reference evidence baselines.
- Mutability: editable before release; after release, changes occur via new versions/releases.

2) `evidence/` — EVIDENCE & proof system (append-oriented)
- Audience: auditors, security/compliance, engineering.
- Content: runs, manifests, indices, verification outputs, reports.
- Mutability: additive by default. Corrections produce new runs/waves/releases.

3) `collateral/` — Field collateral (fast iteration)
- Audience: field, partners, design partners, internal sales engineering.
- Content: decks, demo scripts, pilot offer/SOW drafts, ROI models.
- Mutability: can iterate rapidly, but factual claims must trace to evidence baselines.

## Claim policy (traceability)

Any claim in `official/` or `collateral/` MUST include a traceable evidence baseline:
- wave alias and wave_id
- manifest/policy/index hashes where applicable
- references to specific runs where applicable

Claims without evidence must be explicitly labeled non-verified.

## Source of truth for execution plan

`TRACKING-HARDENING.md` is the canonical execution plan and Definition of Done reference for hardening and repository completion.
