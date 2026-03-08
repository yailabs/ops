# D1-digital/egress-v1 - Digital Domain Pack (Network Egress Control)

This pack defines the semantic meaning of forbidden outbound network egress in the Digital domain.

Canonical source of normative execution logic:
- `law/control-families/digital/*`
- `law/domain-specializations/network-egress/*`

This pack remains:
- a descriptive catalog surface
- a qualification/trial fixture bundle
- an evidence linkage point for RT/QT flows in `ops`

The runtime grammar must remain invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effect (semantic)
- A process inside a workspace attempts to establish an outbound connection to a destination that is not covered by an active contract/allowlist.

## Runtime effect domain (where enforcement happens)
- `network`

## Intended use
- SC-102 (core-only) qualification: prove fail-closed egress blocking + evidence completeness.

## Safety
Vectors use TEST-NET IP ranges (RFC 5737) to avoid real-world targets.

## RealTarget Trials
- Catalog trial spec: `catalog/domains/trials/D1-digital/egress-v1/RT-001-curl-egress-v1/`
- Qualification runner: `evidence/qualification/RT-0.1-001-D1-EGRESS-CURL/`
- Catalog trial spec: `catalog/domains/trials/D1-digital/egress-v1/RT-002-otel-export-egress-v1/`
- Qualification runner: `evidence/qualification/RT-0.1-002-D1-EGRESS-OTEL/`
- Catalog trial spec: `catalog/domains/trials/D1-digital/egress-v1/RT-003-s3-upload-egress-v1/`
- Qualification runner: `evidence/qualification/RT-0.1-003-D1-EGRESS-S3/`

Note:
- Pack files remain semantic law (contracts/reason codes/evidence schema).
- Trial files define executable real-target procedures and runtime-derived evidence.
- Catalog trial spec: `catalog/domains/trials/D1-digital/egress-v1/RT-004-github-issue-comment-egress-v1/`
- Qualification runner: `evidence/qualification/RT-0.1-004-D1-GITHUB-ISSUE-COMMENT/`

## Hierarchy alignment

- Root family: `digital` (internal_id: `D1`)
- Canonical domain seed: `digital.egress`
- Subdomain seed: `digital.egress.default`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `gdpr-eu`, `security-supply-chain`, `retention-governance`.
- Overlay relevance: `gdpr-eu`, `security-supply-chain`, `retention-governance` (and `sector.finance` when financial context exists).

