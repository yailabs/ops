# Governance

This repository has three layers:

1) `official/` — Official documents (release-only)
- Versioned editorially (v0.x, v1.0)
- Must include Evidence Baseline references (wave_id + hashes)

2) `evidence/` — Evidence & proof system (append-only)
- Waves and evidence bundles must never be rewritten
- Fixes create new waves and new references

3) `collateral/` — Field collateral (iterates fast)
- Decks, demo scripts, ROI models, pilot offer/SOW drafts
- Must reference a wave baseline when making claims
