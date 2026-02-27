# D2-physical/actuator-command-v1 — Domain Pack (Actuator Command Authorization)

## Scope
This domain pack defines the **semantic meaning of forbidden actuator commands** in the **Physical (D2)** domain and the evidence/KPI requirements to qualify containment under SC-102.

Runtime grammar invariant:
**trigger → context → authority/contract → decision → enforcement → evidence**

This pack is **safe-by-design**: vectors MUST be executed against a **mock/simulated actuator provider**, not real hardware.

## Problem statement (domain semantics)
In the physical domain, an “actuator command” is a high-consequence external effect. A forbidden actuator command is any command that violates:
- authority/arming requirements, or
- safety window / interlock constraints, or
- target allowlist constraints (device, channel, command class)

The runtime does not “understand physics”; it enforces effects according to this pack.

## Runtime effect domains (enforcement surface)
Primary:
- `providers` (actuator adapter/driver provider)

Optional (recommended for arming):
- `control` (arming/escalation gating)

## Forbidden effects (normative)
A command is forbidden if any of the following holds:

1) **Authority missing**
- No active authority contract for the principal/workspace to issue actuator commands.

2) **Not armed**
- The workspace is not in an armed state for physical actuation (arming required).

3) **Outside safety window**
- The command is issued outside the allowed safety window, or violates an interlock.

4) **Target not contracted**
- The command targets a device/channel not in the contracted allowlist.

## Expected decisions (outcomes + reason codes)
For forbidden commands, the expected outcome is:
- `deny` (default) or `quarantine` (if configured for escalation)

For permitted commands (under allow baseline):
- `allow`

Reason codes MUST be stable once this pack is used for qualification.  
(See `reason-codes.v1.json` for the canonical list.)

## Evidence requirements (what must be recorded)
At minimum, evidence for each decision should include:
- context envelope (`ws_id`, `trace_id`, identity/role, arming state)
- baseline/policy hash
- effect descriptor (actuator target + command)
- decision outcome + reason code
- enforcement result (effect applied or blocked)
- containment metrics (attempted vs succeeded, by target)

The required evidence fields are declared in:
- `evidence.required.v1.json`

## KPIs (minimum)
This pack requires measurement of:
- forbidden command success rate (target: **0**)
- time-to-contain (p50/p95)
- evidence completeness (target: **100%** required fields)
- repeatability (3/3 consistent runs under same baseline)

KPIs are declared in:
- `kpi.v1.json`

## Baselines (contracts)
This pack defines three baselines:
- `contracts/baseline-allow.json` — nominal authorized actuation under contracted targets and safety window
- `contracts/baseline-deny.json` — deny forbidden actuation attempts (fail-closed)
- `contracts/baseline-quarantine.json` — escalate to quarantine on forbidden actuation attempts (simulation-only where quarantine has meaning)

Baselines MUST be hashable and referenced in evidence.

## Vectors (safe execution only)
Vectors define safe, repeatable stimuli and expected outcomes:
- `vectors/attack_profile.safe.json` — simulated actuator command attempts (non-destructive)
- `vectors/expected_outcomes.json` — expected outcomes per baseline

Rule:
- vectors MUST NOT target real hardware. Use a mock provider or simulator adapter.

## Intended use
- SC-102 core qualification via simulated actuator provider (D2 pack semantics).
- Can be extended in later phases to add:
  - multi-step arming workflows
  - richer safety interlocks
  - time-window validation and calibration state checks