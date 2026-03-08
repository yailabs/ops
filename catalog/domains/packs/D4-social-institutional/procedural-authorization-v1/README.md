# D4-social-institutional/procedural-authorization-v1 - Social/Institutional Domain Pack (Procedural Authorization)

This pack defines the semantic meaning of forbidden procedural actions in the Social/Institutional domain.

Runtime grammar invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effects (semantic)
- Executing a procedural step without the required role, delegation, or arming state.
- Executing a step out of order (when the procedure requires sequencing).

## Runtime effect domain (where enforcement happens)
- `control` (procedure-step execution requests)
- optionally `storage` (writing an official act/record without authorization)

## Intended use
- SC-102 (core-only) qualification: prove fail-closed procedural enforcement + evidence completeness.
- Safe by design: vectors are simulated procedure-step requests.

## Canonical normative source and fixture status

- Canonical normative source: `law/control-families/social-institutional` (specializations pending)
- This pack is a qualification fixture bundle for `ops` catalog/trials/evidence.
- It is not the normative source of truth for runtime decisions.

## Hierarchy alignment

- Root family: `social-institutional` (internal_id: `D4`)
- Canonical domain seed: `social-institutional.procedural-authorization`
- Subdomain seed: `social-institutional.procedural-authorization.default`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `retention-governance`.

