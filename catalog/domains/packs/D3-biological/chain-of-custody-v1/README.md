# D3-biological/chain-of-custody-v1 - Biological Domain Pack (Consent & Chain-of-Custody)

This pack defines the semantic meaning of forbidden biological sample/data access under consent and chain-of-custody constraints.

Runtime grammar invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effects (semantic)
- Reading a biological sample record or derived dataset without valid consent.
- Accessing a sample when the chain-of-custody is incomplete or broken.
- Exporting sample data for an undeclared purpose.

## Runtime effect domain (where enforcement happens)
- `storage` (sample/dataset reads and exports)
- optionally `providers` (lab system adapter) and `control` (approval/arming)

## Intended use
- SC-102 (core-only) qualification: prove fail-closed on missing consent/custody + evidence completeness.
- Safe by design: vectors use simulated sample IDs and synthetic metadata (no real patient data).

## Canonical normative source and fixture status

- Canonical normative source: `law/control-families/biological` (specializations pending)
- This pack is a qualification fixture bundle for `ops` catalog/trials/evidence.
- It is not the normative source of truth for runtime decisions.

## Hierarchy alignment

- Root family: `biological` (internal_id: `D3`)
- Canonical domain seed: `biological.chain-of-custody`
- Subdomain seed: `biological.chain-of-custody.default`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `retention-governance`.

