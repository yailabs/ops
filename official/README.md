# OFFICIAL — YAI Document Set

## Scope
This folder contains the official YAI document set (release-oriented). It is the package you can share with:
- procurement and funding stakeholders
- legal and compliance teams
- security and audit functions
- partners / design partners

## Hard requirements
1) **Versioned documents**  
   Each document is editorially versioned (v0.x, v1.0, …) and must carry a front-matter block (see `_templates/FRONT-MATTER.md`).

2) **Evidence Baseline is mandatory**  
   Every OFFICIAL document MUST include an Evidence Baseline section referencing an immutable wave bundle under:
   - `/evidence/waves/`

3) **Claims must be traceable (golden rule)**  
   Any claim made in OFFICIAL must be traceable:
   CLAIM → WAVE (MANIFEST/INDEX) → RUN → POLICY/BASELINE → VERIFY OUTPUT → EVIDENCE FILES

4) **Canonical terminology**  
   OFFICIAL documents MUST use canonical terms from:
   - `official/_glossary/TERMS-v0.1.0.md`

5) **Compliance spine anchoring**  
   Compliance posture and mappings live in:
   - `official/compliance/`

## Read order
Start from `official/index.md`.