# yai-ops — Enterprise Operational Evidence Repository for YAI

`yai-ops` is the canonical operational repository for enterprise validation, qualification evidence, and official publication collateral for the YAI platform.

## Platform role

Dependency and authority chain:

`yai-law` -> `yai-sdk` -> `yai-cli` -> `yai` -> `yai-ops`

`yai-ops` is where conformance, assurance, and field-readiness claims are evidenced.
It does not redefine normative law contracts.

## Repository mission

`yai-ops` is the canonical home for:
- **OFFICIAL**: procurement/funding/partner-ready publication set
- **EVIDENCE + WAVES**: append-only evidence bundles with manifests, indices, verification outputs
- **CATALOG**: scenarios/domains/packs/gates/trials scope model
- **COLLATERAL**: field material aligned to verified evidence baselines

Primary audiences:
1. Procurement and Legal
2. Security/Compliance and Auditors
3. Engineering and Partners

## Golden rule (traceability is mandatory)

Any claim in OFFICIAL or COLLATERAL must be traceable:

`CLAIM -> WAVE (MANIFEST/INDEX) -> RUN -> POLICY/BASELINE -> VERIFY OUTPUT -> EVIDENCE FILES`

Claims lacking evidence traceability must be removed or clearly marked non-verified (and should not appear in OFFICIAL releases).

## Repository layout

- `official/` - versioned official publication set
  - `official/_glossary/` - canonical terminology
  - `official/compliance/` - applicability matrix, crosswalks, evidence mapping
- `evidence/` - append-only evidence system
  - `evidence/waves/` - released wave bundles
  - `evidence/qualification/` - qualification packs and runbooks
  - `evidence/validation/` - audits, benchmarks, proofs
  - `evidence/reports/` - generated reports over evidence
- `catalog/` - scenarios/domains/packs/trials/gates
- `collateral/` - field-facing collateral artifacts
- `schemas/` - normative JSON schemas for produced artifacts
- `research/` - non-binding experiments (not evidence authority)

## Governance boundaries

- Normative contract authority: `yai-law`
- Runtime implementation authority: `yai`
- Operator implementation authority: `yai-cli` / `yai-sdk`
- Governance/tooling factory standards: `yai-infra`
- Operational evidence and publication packaging: `yai-ops`

## Where to start

- `TRACKING-HARDENING.md` - execution plan and definition of done
- `GOVERNANCE.md` - governance and change policy
- `evidence/waves/LATEST` - current verified baseline
- `official/index.md` - procurement/partner publication entry
