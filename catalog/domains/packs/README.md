---
id: DOMAIN-PACKS
title: Domain Packs — Specification & Layout
status: draft
owner: catalog
effective_date: 2026-02-23
revision: 1
---

# Domain Packs

Domain Packs are versioned **semantic packages** that allow YAI to operate coherently across different D-Major domains **without changing the runtime**.

A Domain Pack defines:
- what a **forbidden effect** means in a given domain (domain semantics),
- what **authority/contract constraints** apply,
- which **decision outcomes** and **reason codes** must be emitted,
- which **evidence fields** are required,
- which **KPIs** must be measured,
- and which **safe vectors** (stimuli) can be used for qualification runs.

Domain Packs are **not** runbooks, not audits, and not implementation code.  
They are the "semantic local law + test vectors" used by scenarios (SC) and qualification tracks (QT).

## Relationship to other artifacts
- **D-Major domains** — semantic taxonomy (`catalog/domains/D-MAJOR.md`)
- **SC (Scenario spec)** — declares scenario goal and invariants (`catalog/scenarios/`)
- **QT (Qualification track)** — executes a scenario with one or more packs (`evidence/qualification/QT-*`)
- **RT (RealTarget trial)** — procedure bound to a pack (`catalog/domains/trials/`)
- **Wave bundle** — immutable proof release (`evidence/waves/`)

## Canonical pack identifier (Pack ID)
A pack is referenced by `domain_pack_id`:

- `D1-digital/egress-v1`
- `D5-economic/transaction-authorization-v1`
- `D8-scientific/reproducibility-parameter-lock-v1`

Pack ID format:
`<Dk-folder>/<pack-folder>`

## Naming rules (binding)
### D-Major folder name
Must follow:
- `D1-digital`
- `D2-physical`
- `D3-biological`
- `D4-social-institutional`
- `D5-economic`
- `D6-operational`
- `D7-cognitive-cultural`
- `D8-scientific`
- `D9-environmental-climatological`

### Pack folder name
Must follow:
- `<pack-name>-v<integer>`

Examples:
- `egress-v1`
- `actuator-command-v1`
- `reproducibility-parameter-lock-v1`

## Standard layout (minimum required)
Every pack MUST include the following files:

```text
catalog/domains/packs/<Dk>/<pack-id>/
  README.md                          (recommended)
  pack.meta.json
  reason-codes.v1.json
  evidence.required.v1.json
  kpi.v1.json
  contracts/
    baseline-allow.json
    baseline-deny.json
    baseline-quarantine.json
  vectors/
    attack_profile.safe.json
    expected_outcomes.json
```

## File roles (normative)

### `pack.meta.json` (required)

Defines pack identity and semantics:

* `id`, `d_major`, `title`, `version`
* `forbidden_effects[]` (domain semantics)
* `primary_runtime_effect_domain` (where enforcement is expected)
* `runtime_grammar_steps[]` (should remain the same grammar chain)

Recommended fields (if present):

* `revision` (increment for non-breaking editorial updates)
* `links` (scenario/trial pointers)

### `reason-codes.v1.json` (required)

Defines stable decision explanations:

* keys are reason code identifiers (stable strings)
* each entry declares:
  * default outcome (allow/deny/quarantine/fail)
  * severity (informational/low/medium/high/critical)
  * description

Rule:

* Reason codes MUST remain stable once a pack is used for qualification (changes require a new pack version).

### `evidence.required.v1.json` (required)

Defines evidence completeness requirements:

* list of required fields emitted by the runtime/evidence pipeline
* used by qualification tooling to validate evidence completeness

Rule:

* adding/removing required fields is a breaking change → new pack version.

### `kpi.v1.json` (required)

Defines KPIs required for qualification:

* which metrics must be measured
* optional thresholds or ranges
* optional "must be present" vs "optional" classification

Rule:

* KPI changes affecting pass/fail require a new pack version.

### `contracts/` (required)

Baselines that drive decisions:

* `baseline-allow.json` — nominal behavior
* `baseline-deny.json` — blocks forbidden effects
* `baseline-quarantine.json` — escalates to quarantine for forbidden effects (or specified patterns)

Rule:

* baselines MUST be hashable and recorded in evidence (baseline hash / policy hash).

### `vectors/` (required)

Safe stimuli and expected results:

* `attack_profile.safe.json` — stimulus definition (safe/non-destructive)
* `expected_outcomes.json` — expected decision/enforcement outcomes for the stimulus

Rule:

* vectors are designed to be executed repeatedly and publicly.

## Where execution procedures live (important)

Execution procedures are not part of packs. They are defined in:

* Catalog trial specs: `catalog/domains/trials/`
* Qualification evidence harnesses: `evidence/qualification/RT-*` and `evidence/qualification/QT-*` (where applicable)

## Optional (recommended) additions

You MAY add:

* `schema/` — JSON schema definitions for pack files
* `fixtures/` — sample data for local runs
* `adapters/` — notes for domain-specific adapters (physical/biological/etc.)

## Versioning policy (binding)

Packs are versioned at folder level: `*-v1`, `*-v2`, …

A new version is required if any of the following change in a way that impacts qualification outcomes:

* reason codes
* required evidence fields
* baseline semantics
* forbidden effect definition
* expected outcomes for vectors

Minor editorial edits that do not affect pass/fail may remain within the same version, but should be tracked via a `revision` field in `pack.meta.json` (if used).

## Qualification expectations (SC102 alignment)

For SC102 (core-only) the following invariants must hold for every pack:

* decisions are stable (`outcome + reason_code`)
* fail-closed enforcement on forbidden effects
* evidence completeness per `evidence.required.v1.json`
* repeatability: 3 consecutive runs consistent under the same baseline (where applicable)

The pack defines semantics; the runtime preserves the grammar.

## Security and safety rules

* Vectors MUST be safe and non-destructive.
* No real secrets in pack files.
* If a pack models a harmful real-world action (e.g., physical actuation), the vector must be simulated (adapter event), not a real command to hardware.

## Creating a new pack (procedure)

1. Choose `Dk` and define the forbidden effect semantics.
2. Define stable reason codes (2–5, minimal but complete).
3. Define required evidence fields.
4. Define KPIs (minimum set).
5. Provide baselines (allow/deny/quarantine).
6. Add a safe vector and expected outcomes.
7. Reference the pack in:
   * the relevant `SC-xxx` scenario spec, and
   * the relevant qualification plan/gate.

## SC102 rollout planning

* `catalog/domains/packs/SC102-DOMAIN-ROLLOUT-WAVES-v0.1.0.md`