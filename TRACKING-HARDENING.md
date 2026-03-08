# Hardening & Standards Baseline — YAI Ops Repo (v0.1.0)

## Target (fixed)
This repo must be readable and actionable for:
1) Procurement + Legal (OFFICIAL)
2) Security/Compliance + Auditor (EVIDENCE/WAVES + verify)
3) Engineering/Partner (CATALOG + SCHEMAS + TOOLS)

## Output packages (fixed)
A) OFFICIAL — procurement/bids/partners ready, stand-alone narrative + claims.
B) EVIDENCE + WAVES — forensic, reproducible, verifiable release bundles.
C) CATALOG — scope map: domains/packs/gates/scenarios.

## Golden rule (binding)
Every OFFICIAL claim MUST be traceable:
CLAIM → WAVE (MANIFEST/INDEX) → RUN → POLICY/BASELINE → VERIFY OUTPUT → EVIDENCE FILES

If not traceable: remove or mark explicitly as non-verified (avoid in OFFICIAL).

## Compliance spine (structure)
- CORE: AI Act, GDPR, (ePrivacy where applicable), ISO/IEC 42001, ISO/IEC 23894, NIST AI RMF,
        ISO/IEC 27001/27002 baseline, NIST SSDF + SLSA supply-chain.
- OVERLAYS (triggered): CRA, NIS2, DORA, Data Act + DGA, cloud privacy/security (27017/27018/27701).

## Repo invariants (apply everywhere)
1) Scope / Audience / Non-goals / Definitions in any serious doc.
2) Strict separation: official vs evidence vs research.
3) Versioning + compatibility declarations for OFFICIAL docs and schemas.
4) Chain-of-custody: wave manifest/index/verify are mandatory.
5) Legal hygiene: posture + process + evidence (no legal advice language).

## Order of operations (execution plan)
A) Root docs (README/GOVERNANCE/PUBLISHING + this tracking)
B) official: index + README + templates + glossary
C) official/compliance: applicability + crosswalks + evidence map
D) official: overview → tech dossier → assurance → delivery → industrial plan → legal-pack
E) catalog
F) collateral
G) schemas
H) evidence/waves hardening
I) research boundaries

## Definition of Done (repo-level)
- OFFICIAL is stand-alone and points to evidence precisely.
- Crosswalks filled at least for primary claims (AI Act + privacy + security/supply chain).
- Every wave has MANIFEST.json + INDEX.md + verify output, consistently.
- Single canonical glossary reused everywhere.
- v1 schemas exist for produced artifacts.
- law referenced as authoritative internal baseline (incorporation by reference).
