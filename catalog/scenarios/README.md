# Scenarios

Scenario specifications define **qualification targets** and **invariants**.  
They describe “what must be proven” and “what must remain invariant,” not how the implementation is built.

## What a scenario is
A scenario:
- declares the goal (what is being proven)
- defines invariants (what must remain true)
- selects relevant D-Major domains and domain packs
- binds to qualification gates (QT) and expected outputs

Scenarios do not contain implementation procedures.

## Where procedures live
Execution and implementation sequencing belong to:
- catalog trial runbooks: `catalog/domains/trials/**/runbook/steps.md`
- qualification evidence harnesses: `evidence/qualification/`
- core program runbooks (engineering): `docs/program/23-runbooks/` (if present in the wider ecosystem)

## Current scenarios
- `SC-102.md` — core contain-to-evidence gate (cross-domain, no mind)
- `SC-103-mind-integrated-remediation.md` — advanced gate with cognition/agentic surfaces (mind-integrated)

## Rules
1) Scenarios define expected behavior and invariants, not implementation.
2) A scenario is “proven” only through evidence produced by qualification gates and (optionally) promoted into waves.
3) OFFICIAL claims must reference evidence; evidence must trace back to scenario + pack + trial definitions.