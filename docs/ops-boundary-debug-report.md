# Ops Boundary Debug Report

Date: 2026-03-08
Scope: boundary integrity of `ops` after first refactor wave

## Executive verdict

`ops` boundary is significantly improved, but domain packs still carry heavy quasi-normative payload that can reintroduce ambiguity.

- Strong: repo identity as bureau is clear in root docs/governance.
- Risk: packs still include extensive `contracts/baseline-*.json` semantics across all domains, which may be interpreted as active policy authority if not tightly framed.

## Classification by area

### Repository identity

- `README.md`: **Approved**
- `GOVERNANCE.md`: **Approved as scaffold**
- `docs/repository-scope.md`: **Approved**

Finding:
- Cross-repo role is explicit (`law` normative, `yai` runtime, `ops` bureau).
- Still mentions transitional quarantine paths that were removed earlier in this wave.

### catalog/

- `catalog/README.md`: **Approved as scaffold**
- `catalog/domains/packs/README.md`: **Approved as scaffold**
- D1/D8 pack READMEs: **Approved as scaffold**
- Remaining packs (D2..D9): **Semantically unresolved**

Evidence:
- 27 baseline contract files remain under pack contracts.
- D1/D8 explicitly point to `law/domains/*` as canonical source.
- Many other packs still read as substantive policy artifacts, not just qualification fixtures.

### qualification/

- `qualification/README.md`: **Approved as scaffold**
- `evidence/qualification/README.md`: **Approved as scaffold**

Finding:
- Boundary wording is now correct, but fixture/policy semantics are still dense in historical pack assets.

### evidence/

- `evidence/README.md`: **Approved as scaffold**
- Evidence corpus: **Approved** for bureau role

Finding:
- Evidence role is clear; canonical normativity is not claimed.

### official/ and collateral/

- `official/`: **Approved**
- `collateral/`: **Approved**

No major boundary faults detected.

## Remaining ambiguity

1. Pack contract payloads are still semantically rich enough to be mistaken for canonical policy source.
2. D1/D8 are well-framed; D2..D9 need the same explicit canonical-law linkage.
3. Some transitional wording references cleanup paths already removed.

## Recommended cleanup before heavy verticalization

1. Add explicit canonical-law pointers (`law/domains/<id>`) to all non-D1/D8 pack READMEs and pack metadata.
2. Introduce explicit fixture watermark in pack `contracts/` files (`qualification_fixture: true`, `canonical_ref: law/...`).
3. Keep pack contracts for qualification, but prevent “normative source” interpretation by schema-level metadata.

## Bucket summary

### Approved and stable
- Root identity (`README`, scope, governance).
- official/collateral/evidence publication posture.

### Approved as scaffold
- catalog and qualification guidance.

### Needs refoundation before verticalization
- Pack semantics contract framing for D2..D9.

### Needs mass verticalization
- Domain-pack coherence with law refs across all domains.

### Legacy contamination to remove
- Transitional wording pointing to removed quarantine paths.

### Narrative ambiguity to close
- Ensure pack contracts are unambiguously “qualification fixture” artifacts.
