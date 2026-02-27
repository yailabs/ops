# yai-ops

Operational repository for YAI. This repo contains the official document set, verifiable evidence bundles (waves), qualification assets, validation outputs, reports, and field collateral.

## Purpose
yai-ops is the canonical home for:
- **OFFICIAL**: procurement / funding / partner-ready document set (versioned)
- **EVIDENCE + WAVES**: append-only evidence bundles with manifests, indices, and verification outputs
- **CATALOG**: scope map (scenarios, domains, packs, gates, trials)
- **COLLATERAL**: field collateral (deck, demo scripts, pilot offer, ROI, SOW) aligned to evidence baselines

This repository is designed to be readable and actionable for:
1) Procurement + Legal (OFFICIAL)
2) Security/Compliance + Auditor (EVIDENCE/WAVES + verify)
3) Engineering/Partner (CATALOG + SCHEMAS + TOOLS)

## Golden rule (claims must be traceable)
Any claim made in OFFICIAL or COLLATERAL MUST be traceable to evidence:

CLAIM → WAVE (MANIFEST/INDEX) → RUN → POLICY/BASELINE → VERIFY OUTPUT → EVIDENCE FILES

If a claim is not traceable, it must be removed or explicitly marked as non-verified (OFFICIAL should avoid non-verified claims).

## Repository layout
- `official/` — versioned official document set (procurement / bids / partners)
  - `official/_glossary/` — canonical terms used across the repo
  - `official/compliance/` — applicability matrix + crosswalks + evidence mapping
- `evidence/` — append-only evidence system
  - `evidence/waves/` — wave releases (manifest, index, verify output, referenced runs)
  - `evidence/qualification/` — qualification packs, demos, runbooks
  - `evidence/validation/` — audits, benchmarks, proofs
  - `evidence/reports/` — reports generated from evidence bundles
- `catalog/` — scenarios, domains, packs, trials, gates
- `collateral/` — deck, executive brief, demo script, pilot offer, ROI model, SOW
- `schemas/` — normative JSON schemas for produced artifacts
- `research/` — non-binding experiments; must not be used to justify OFFICIAL claims unless promoted into EVIDENCE/WAVES

## Where to start
- Read `TRACKING-HARDENING.md` for the execution plan and Definition of Done.
- For the latest verified release baseline, start from `evidence/waves/LATEST` and the referenced wave `INDEX.md`.
- For procurement-ready material, start from `official/index.md`.