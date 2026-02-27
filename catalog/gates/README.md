# Qualification Gates

Qualification gates are **executable pass/fail checkpoints** bound to scenario specifications.  
They exist to prevent “demo drift” by requiring reproducible evidence before anything is promoted into reports and waves.

## What a gate is
A gate is a named checkpoint with:
- a scenario scope (SC-xxx)
- one or more domain packs and trials
- a fixed set of mandatory checks (hard fail if missing)
- evidence outputs required for closure

A gate is closed only when the required checks pass and evidence artifacts are complete.

## Registry
- Gate registry: `catalog/gates/QUALIFICATION-GATES-v0.1.0.md`

## Primary runtime gates (current)
- `QT-0.1-001-SC102` — Core Gate A (runtime governance without cognition)
- `QT-0.1-002-SC103` — Mind/Cognition Gate B (governed cognition integration)

## Closure rules (binding)
1) Gate closure requires reproducible evidence (runs are repeatable under the same baseline).
2) Mandatory checks cannot close on `SKIP`.
3) If a check fails, remediation creates new runs and (if promoted) new waves — evidence is append-only.
4) Any OFFICIAL claim must be traceable to a closed gate through a wave/run chain.

## Evidence linkage
Typical evidence locations:
- Qualification packs: `evidence/qualification/QT-*`
- Trial runs: `evidence/qualification/RT-*`
- Wave bundles (release artifacts): `evidence/waves/*`