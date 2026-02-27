---
id: DOMAIN-TRIALS
title: Domain RealTarget Trials — Catalog Layer
status: draft
owner: catalog
effective_date: 2026-02-24
revision: 1
---

# Domain RealTarget Trials

Trials define repeatable procedures that exercise **real targets** under a Domain Pack's governance.

A trial answers:
- what is executed (target + procedure),
- under which domain semantics (pack + baselines),
- what evidence must be produced,
- and what outcomes are expected (deny/allow + reason codes + KPIs).

## Roles (pack vs trial vs qualification)
- **Domain packs** remain semantic law:
  - forbidden effects
  - reason codes
  - baselines (allow/deny/quarantine)
  - required evidence fields
  - KPI definitions
  - vectors and expected outcomes
- **Trials** define the real execution procedure and evidence extraction plan:
  - target metadata
  - runbook steps
  - how evidence fields/KPIs are collected
- **Qualification runners** execute trials and produce auditable bundles:
  - run directories
  - decision records
  - metrics
  - evidence indices
  - wave promotion artifacts (when applicable)

## Canonical layout (binding)
Catalog trial specifications live here:
- `catalog/domains/trials/<Dk>/<pack>/<RT-id>/`

Qualification runner material lives under evidence:
- `evidence/qualification/RT-*` and `evidence/qualification/QT-*`

Rule:
- The catalog defines **what a trial is**.
- The evidence tree contains **what happened**.

## Trial folder layout (minimum required)
Each trial SHOULD contain at minimum:

```text
catalog/domains/trials/<Dk>/<pack>/<RT-id>/
  README.md
  trial.meta.json
  target/
    target.meta.json
  runbook/
    steps.md
  evidence.required.v1.json   (optional override; if absent, inherit from pack)
  kpi.v1.json                 (optional override; if absent, inherit from pack)
```

## Notes
* Overrides should be rare. Prefer inheriting from the pack unless a target requires extra evidence.
* Trial IDs should remain stable once used for qualification.

## How trials map to evidence and waves
* A trial is executed by a qualification runner, producing a run directory (evidence).
* A set of runs can be promoted into a wave bundle.
* OFFICIAL claims reference waves; waves reference runs; runs reference trials/packs.

Chain: `OFFICIAL claim → wave → run → trial → pack → domain semantics`

## Current live trials
* `D1-digital/egress-v1/RT-001-curl-egress-v1`
* `D1-digital/egress-v1/RT-002-otel-export-egress-v1`
* `D1-digital/egress-v1/RT-003-s3-upload-egress-v1`
* `D1-digital/egress-v1/RT-004-github-issue-comment-egress-v1`
* `D8-scientific/reproducibility-parameter-lock-v1/RT-001-params-lock-v1`