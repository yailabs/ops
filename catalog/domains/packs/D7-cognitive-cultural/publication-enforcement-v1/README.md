# D7-cognitive-cultural/publication-enforcement-v1 - Cognitive/Cultural Domain Pack (Publication & Enforcement)

This pack defines the semantic meaning of forbidden publication/visibility changes in the Cognitive/Cultural domain.

Runtime grammar invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effects (semantic)
- Publishing content without required provenance.
- Changing visibility/ranking without policy basis.
- Enforcing moderation actions without contestability metadata (appeal path/decision trace).

## Runtime effect domain (where enforcement happens)
- `providers` (content platform adapter/publishing provider)
- optionally `storage` (writing immutable provenance records)
- optionally `control` (high-impact actions requiring arming)

## Intended use
- SC-102 (core-only) qualification: prove fail-closed publication governance + evidence completeness.
- Safe by design: vectors are simulated content actions, no real public publishing.

## Canonical normative source and fixture status

- Canonical normative source: `law/control-families/cognitive-cultural` (specializations pending)
- This pack is a qualification fixture bundle for `ops` catalog/trials/evidence.
- It is not the normative source of truth for runtime decisions.

## Hierarchy alignment

- Root family: `cognitive-cultural` (internal_id: `D7`)
- Canonical domain seed: `cognitive-cultural.publication-enforcement`
- Subdomain seed: `cognitive-cultural.publication-enforcement.default`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `retention-governance`.

