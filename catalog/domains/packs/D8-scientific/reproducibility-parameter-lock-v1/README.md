# D8-scientific/reproducibility-parameter-lock-v1 - Scientific Domain Pack (Reproducibility Parameter Lock)

This pack defines the semantic meaning of non-reproducible scientific pipeline execution.

Canonical source of normative execution logic:
- `law/control-families/scientific/*`
- `law/domain-specializations/parameter-governance/*`
- `law/domain-specializations/reproducibility-control/*`

This pack remains:
- a descriptive catalog surface
- a qualification/trial fixture bundle
- an evidence linkage point for RT/QT flows in `ops`

Runtime grammar invariant:
trigger -> context -> authority/contract -> decision -> enforcement -> evidence

## Forbidden effects (semantic)
- Running an experiment/simulation/pipeline step without a declared parameter lock (params hash).
- Running with undeclared exclusions or transformations that break reproducibility.

## Runtime effect domain (where enforcement happens)
- `control` (pipeline run requests)
- optionally `storage` (publishing results without provenance)

## Intended use
- SC-102 (core-only) qualification: prove fail-closed on missing reproducibility lock + evidence completeness.
- Safe by design: vectors are simulated pipeline runs (no external side effects required).
## RealTarget Trials
- `catalog/domains/trials/D8-scientific/reproducibility-parameter-lock-v1/RT-001-params-lock-v1`
- Qualification runner: `evidence/qualification/RT-0.1-001-D8-PARAMS-LOCK/`

## Canonical normative source and fixture status

- Canonical normative source: `law/control-families/scientific` + `law/domain-specializations/reproducibility-control`
- This pack is a qualification fixture bundle for `ops` catalog/trials/evidence.
- It is not the normative source of truth for runtime decisions.

## Hierarchy alignment

- Root family: `scientific` (internal_id: `D8`)
- Canonical domain seed: `scientific.reproducibility-parameter-lock`
- Subdomain seed: `scientific.reproducibility-parameter-lock.default`
- This pack is a scenario/qualification class fixture in `ops`; canonical ontology lives in `law`.

## Compliance linkage

- Compliance layers are canonical in `law/overlays/regulatory/*` + `law/overlays/sector/*` and compose with domain policy at runtime.
- This pack references compliance context for qualification only; it does not define compliance canonically.
- Referenced compliance: `ai-act`, `gdpr-eu`, `retention-governance`, `security-supply-chain`.
- Overlay relevance: `ai-act` (high-risk/oversight), `security-supply-chain`, `retention-governance`, and sector overlays (`healthcare`, `finance`) when applicable.

