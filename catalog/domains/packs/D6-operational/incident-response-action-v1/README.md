# D6-operational/incident-response-action-v1 - Operational Domain Pack (Incident Response Actions)

This pack defines the semantic meaning of forbidden operational actions in the Operational domain,
with a focus on incident response / SRE-style containment actions.

Runtime grammar invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effects (semantic)
- Executing a high-impact operational action (e.g., isolate host, revoke credentials, block egress)
  without required escalation and arming.
- Executing actions outside the allowed maintenance/response window.
- Executing actions in an unauthorized scope (e.g., production) without sufficient authority.

## Runtime effect domain (where enforcement happens)
- `control` (action request admission)
- `providers` (ops adapter, e.g., firewall/EDR/SOAR mock provider)

## Intended use
- SC-102 (core-only) qualification: prove fail-closed action governance + evidence completeness.
- Safe by design: vectors MUST be simulation-only; no real infra changes.

## Canonical normative source and fixture status

- Canonical normative source: `law/control-families/operational` (specializations pending)
- This pack is a qualification fixture bundle for `ops` catalog/trials/evidence.
- It is not the normative source of truth for runtime decisions.

## Hierarchy alignment

- Root family: `operational` (internal_id: `D6`)
- Canonical domain seed: `operational.incident-response-action`
- Subdomain seed: `operational.incident-response-action.default`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `retention-governance`.

