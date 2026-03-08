# Catalog

The catalog is the operational map of **what YAI proves**, **how it is tested**, and **how it scales** across domains.

It is intentionally separated from:
- `official/` (procurement-ready documents)
- `evidence/` (append-only proof artifacts: waves/runs/reports)
- `research/` (non-binding exploration)

## What lives here
- **Scenarios** — end-to-end stories with clear boundaries (e.g., SC102, SC103)
- **Domain packs** — reusable capability units (policy baselines, reason codes, KPIs, evidence requirements)
- **Trials** — executable test definitions bound to packs (targets, runbooks, expected outcomes)
- **Qualification gates** — acceptance rules for promoting results into waves and reports

## Who uses this
- `evidence/qualification/` — QT/RT qualification packs reference catalog packs and trials
- `evidence/waves/` — wave bundles reference pack baselines and run outcomes
- `official/` — claims reference evidence, which is traceable back to catalog definitions

## Normative baseline (law)
Normative definitions (contracts, invariants, compliance baselines) live in **law** and are incorporated by reference.  
This catalog contains **operational** definitions for qualification and delivery, aligned to that baseline.

## Navigation
- Scenarios: `catalog/scenarios/`
- Domains and packs: `catalog/domains/`
- Trials: `catalog/domains/trials/`
- Qualification gates: `catalog/gates/`

## Rules
1) The catalog may evolve over time.
2) Evidence waves are immutable. If a catalog change requires new proof, publish a new wave.
3) Each pack must define:
   - baselines (allow/deny/quarantine)
   - reason codes
   - KPIs
   - required evidence
   - vectors / expected outcomes
4) Each trial must define:
   - target
   - runbook steps
   - expected outcomes and required evidence