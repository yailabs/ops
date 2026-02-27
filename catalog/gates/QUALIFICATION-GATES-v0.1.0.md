---
id: QUALIFICATION-GATES-v0.1.0
title: Qualification Gates — v0.1.0
status: draft
owner: program-delivery
effective_date: 2026-02-23
revision: 2
---

# Qualification Gates — v0.1.0

## Scope
This registry defines the official **qualification gates (QT)** used to qualify YAI v0.1.x.  
Gates are parameterized by **Domain Packs (D-Major)** while the runtime grammar remains invariant.

Runtime grammar invariant:
**trigger → context → authority/contract → decision → enforcement → evidence**

## Gate registry (v0.1.x)

| Gate (QT) | Scenario (SC) | D-Major coverage | Qualification label | Runtime effect domains | Minimum evidence | Output |
|---|---|---|---|---|---|---|
| `QT-0.1-001-SC102` | `SC-102` | v0.1 baseline: at least **D1** (extendable to D1..D9) | Core-qualified (Gate A) | control, workspace, providers/network/storage/resource, audit/evidence | 3 consistent runs per pack + KPI + evidence index | Qualification pack + metrics summary + (optional) wave promotion |
| `QT-0.1-002-SC103` | `SC-103` | depends on SC102 baseline + selected D-Major packs | Premium-qualified (Gate B) | Gate A + mind/cognition + rollout governance | 3 consistent runs + patch/PR evidence + rollout logs | Qualification pack (incident + remediation) + evidence bundle |

## Qualification rules (binding)
1) **Core-qualified (v0.1)**  
`QT-0.1-001-SC102` = PASS on at least one pack (recommended baseline: D1).

2) **Cross-domain qualified**  
`QT-0.1-001-SC102` = PASS across a defined set of packs spanning multiple D-Major domains (up to D1..D9).  
The runtime grammar must remain invariant; only pack semantics change.

3) **Premium-qualified (v0.1)**  
`QT-0.1-001-SC102` = PASS AND `QT-0.1-002-SC103` = PASS.

## Evidence requirements (minimum)
For a gate to be closed, minimum evidence must include:
- run directories with required artifacts
- evidence index (human + optional machine index)
- KPI capture (as defined by the pack/trial)
- verification outputs for the run (or wave if promoted)

Rule:
- mandatory checks cannot close on `SKIP`
- failures are remediated by producing new runs (append-only evidence)

## Delivery program note
Runbooks, milestone packs, and wave plans should reference these gates as target states.
A wave promotion is valid only when it can be traced to a closed gate through:
**gate → trial → run → wave → OFFICIAL claim**