# D5-economic/transaction-authorization-v1 - Economic Domain Pack (Transaction Authorization)

This pack defines the semantic meaning of forbidden transaction authorization in the Economic domain.

Runtime grammar invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effect (semantic)
- A transaction authorization is requested for an amount/counterparty not covered by an active contract, policy, or limit set.

## Runtime effect domain (where enforcement happens)
- `providers` (payment rails / bank gateway / PSP adapter)
- optionally `control` (approval/arming workflows)

## Intended use
- SC-102 (core-only) qualification: prove fail-closed authorization decisions + evidence completeness.
- Designed to be safe: no real payments are executed; vectors are simulated authorization requests.

## Canonical normative source and fixture status

- Canonical normative source: `law/control-families/economic` + `law/domain-specializations/payments`
- This pack is a qualification fixture bundle for `ops` catalog/trials/evidence.
- It is not the normative source of truth for runtime decisions.

## Hierarchy alignment

- Root family: `economic` (internal_id: `D5`)
- Canonical domain seed: `economic.transaction-authorization`
- Subdomain seed: `economic.transaction-authorization.default`
- Linked wave-1 specializations: `payments`, `transfers`, `settlements`, `fraud-risk-controls`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `retention-governance`, `security-supply-chain`, `sector.finance`.
- Overlay relevance: `sector.finance` (primary), `retention-governance`, `security-supply-chain`, and `gdpr-eu` where personal data is involved.

