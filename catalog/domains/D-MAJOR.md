---
id: D-MAJOR
title: Macro Domains (D-Major) — Cross-Domain Coherence
status: active
owner: catalog
effective_date: 2026-02-23
revision: 1
---

# YAI — Macro Domains (D-Major)

This document defines the nine macro domains used to drive YAI’s cross-domain coherence.

## Purpose
D-Major exists to prove a single point: **YAI is infrastructure**, not a vertical tool.

Across all domains, YAI preserves a single runtime grammar:

**trigger → context → authority/contract → decision → enforcement → evidence**

What changes across domains is the **semantics**, captured through **Domain Packs**.

## D1 — Digital (Compute & Information)
Everything natively made of bits: compute, storage, networking, protocols, distributed systems, software supply chain, APIs, runtimes.

Typical events:
- message ingress, RPC frames, state commits
- network connections, provider calls
- filesystem reads/writes, database queries
- build/release actions, dependency changes

Why it matters:
This domain is closest to the runtime’s native control surface and is typically first for qualification (e.g., SC102 core-only).

## D2 — Physical (Matter, Energy, Space-Time)
Systems where actions move matter/energy and are constrained by physics: sensors/actuators, cyber-physical systems, vehicles, robotics, industrial control, energy, avionics/space.

Typical events:
- telemetry and sensor readings
- actuator commands, safety interlocks
- physical faults, degradation, environmental latency

Why it matters:
Enforcement can have immediate real-world consequences. Domain semantics must encode safety windows, interlocks, and fail-closed boundaries.

## D3 — Biological (Life)
Clinical, biotech, wet-lab processes, bioinformatics, ecosystems.

Typical events:
- measurements, lab protocols, sample handling
- consent capture, chain-of-custody updates
- results, transformations, dataset access

Why it matters:
Authority and evidence must support consent and chain-of-custody constraints, not only access control.

## D4 — Social/Institutional (People & Institutions)
People, institutions, and procedures: law, public administration, governance, regulation, education, labor, welfare.

Typical events:
- formal acts, procedural steps, approvals
- access requests, delegations, notifications
- disputes, accountability events

Why it matters:
Semantics are procedural: a decision must be tied to roles, duties, and procedural legitimacy, not only allow/deny.

## D5 — Economic (Value & Exchange)
Finance, credit, payments, insurance, contracts, procurement, markets.

Typical events:
- authorization/denial, scoring, holds/releases
- transactions, settlement steps, contractual conditions
- disputes and reversals

Why it matters:
This domain is strict about limits, counterparties, and contractual scope. Evidence must support audit and dispute resolution.

## D6 — Operational (Coordination & Logistics)
Coordination of complex systems: logistics, planning, maintenance, incident response, SRE/ops, emergencies.

Typical events:
- scheduling, prioritization, allocation
- rerouting, failover, recovery actions
- escalation and post-incident evidence

Why it matters:
Time-to-action becomes money. Packs must define what requires arming/escalation and what can be automated safely.

## D7 — Cognitive/Cultural (Meaning & Media)
Meaning, content, and cultural dynamics: media, communication, reputation, moderation, knowledge operations.

Typical events:
- publication/visibility changes, ranking decisions
- enforcement actions, access restrictions
- provenance checks, appeals/contestation

Why it matters:
Semantics revolve around provenance, policy compliance, and contestability. Evidence must make decisions auditable and explainable.

## D8 — Scientific (Knowledge & Measurement)
Science as a chain of measurements and transformations: experiments, simulations, pipelines, reproducibility.

Typical events:
- data acquisition, preprocessing, exclusions
- parameter declarations, transformations
- results publication with evidence

Why it matters:
Reproducibility is a core constraint. Packs must encode parameter locks, provenance, and evidence supporting repeatability.

## D9 — Environmental/Climatological (Earth Systems)
Environmental and climatological systems where information is produced by measurement and models across space-time:
environment monitoring, climate analytics, emissions tracking, hazard detection, early warning systems.

Typical events:
- telemetry ingestion (air quality, temperature, water levels, radiation)
- calibration updates, station integrity checks
- derived metrics (AQI, anomaly scores), threshold crossings
- model runs/forecasts with parameter sets
- publication of alerts, bulletins, regulatory reports

Why it matters:
This domain is high-stakes and multi-scale: small integrity failures can cascade into wrong operational decisions or compliance exposure.
Packs must enforce measurement integrity (calibration, provenance) and reproducibility (parameter locks), while minimizing disclosure (e.g., sensitive location data).

## Cross-domain coherence (SC102 alignment note)
SC102 (core-only qualification) demonstrates that these invariants remain stable across D1–D9:

- authority envelope integrity
- policy/contract chain (baseline is hashable/pinnable)
- decision vocabulary stability (allow/deny/quarantine/rate_limit where defined)
- fail-closed behavior for forbidden effects
- evidence pack completeness and replayability
- minimal disclosure (only necessary information emitted)

Only domain semantics change (via Domain Packs), not the runtime grammar.

## Domain packs (canonical location)
Domain packs are defined under:
`catalog/domains/packs/<Dk>/<pack-id>/`

Each pack must declare:
- forbidden effects (domain semantics)
- expected reason codes
- required evidence fields and KPIs
- baselines (allow/deny/quarantine)
- safe vectors (stimuli) and expected outcomes---
id: D-MAJOR
title: Macro Domains (D-Major) — Cross-Domain Coherence
status: active
owner: catalog
effective_date: 2026-02-23
revision: 1
---

# YAI — Macro Domains (D-Major)

This document defines the nine macro domains used to drive YAI’s cross-domain coherence.

## Purpose
D-Major exists to prove a single point: **YAI is infrastructure**, not a vertical tool.

Across all domains, YAI preserves a single runtime grammar:

**trigger → context → authority/contract → decision → enforcement → evidence**

What changes across domains is the **semantics**, captured through **Domain Packs**.

## D1 — Digital (Compute & Information)
Everything natively made of bits: compute, storage, networking, protocols, distributed systems, software supply chain, APIs, runtimes.

Typical events:
- message ingress, RPC frames, state commits
- network connections, provider calls
- filesystem reads/writes, database queries
- build/release actions, dependency changes

Why it matters:
This domain is closest to the runtime’s native control surface and is typically first for qualification (e.g., SC102 core-only).

## D2 — Physical (Matter, Energy, Space-Time)
Systems where actions move matter/energy and are constrained by physics: sensors/actuators, cyber-physical systems, vehicles, robotics, industrial control, energy, avionics/space.

Typical events:
- telemetry and sensor readings
- actuator commands, safety interlocks
- physical faults, degradation, environmental latency

Why it matters:
Enforcement can have immediate real-world consequences. Domain semantics must encode safety windows, interlocks, and fail-closed boundaries.

## D3 — Biological (Life)
Clinical, biotech, wet-lab processes, bioinformatics, ecosystems.

Typical events:
- measurements, lab protocols, sample handling
- consent capture, chain-of-custody updates
- results, transformations, dataset access

Why it matters:
Authority and evidence must support consent and chain-of-custody constraints, not only access control.

## D4 — Social/Institutional (People & Institutions)
People, institutions, and procedures: law, public administration, governance, regulation, education, labor, welfare.

Typical events:
- formal acts, procedural steps, approvals
- access requests, delegations, notifications
- disputes, accountability events

Why it matters:
Semantics are procedural: a decision must be tied to roles, duties, and procedural legitimacy, not only allow/deny.

## D5 — Economic (Value & Exchange)
Finance, credit, payments, insurance, contracts, procurement, markets.

Typical events:
- authorization/denial, scoring, holds/releases
- transactions, settlement steps, contractual conditions
- disputes and reversals

Why it matters:
This domain is strict about limits, counterparties, and contractual scope. Evidence must support audit and dispute resolution.

## D6 — Operational (Coordination & Logistics)
Coordination of complex systems: logistics, planning, maintenance, incident response, SRE/ops, emergencies.

Typical events:
- scheduling, prioritization, allocation
- rerouting, failover, recovery actions
- escalation and post-incident evidence

Why it matters:
Time-to-action becomes money. Packs must define what requires arming/escalation and what can be automated safely.

## D7 — Cognitive/Cultural (Meaning & Media)
Meaning, content, and cultural dynamics: media, communication, reputation, moderation, knowledge operations.

Typical events:
- publication/visibility changes, ranking decisions
- enforcement actions, access restrictions
- provenance checks, appeals/contestation

Why it matters:
Semantics revolve around provenance, policy compliance, and contestability. Evidence must make decisions auditable and explainable.

## D8 — Scientific (Knowledge & Measurement)
Science as a chain of measurements and transformations: experiments, simulations, pipelines, reproducibility.

Typical events:
- data acquisition, preprocessing, exclusions
- parameter declarations, transformations
- results publication with evidence

Why it matters:
Reproducibility is a core constraint. Packs must encode parameter locks, provenance, and evidence supporting repeatability.

## D9 — Environmental/Climatological (Earth Systems)
Environmental and climatological systems where information is produced by measurement and models across space-time:
environment monitoring, climate analytics, emissions tracking, hazard detection, early warning systems.

Typical events:
- telemetry ingestion (air quality, temperature, water levels, radiation)
- calibration updates, station integrity checks
- derived metrics (AQI, anomaly scores), threshold crossings
- model runs/forecasts with parameter sets
- publication of alerts, bulletins, regulatory reports

Why it matters:
This domain is high-stakes and multi-scale: small integrity failures can cascade into wrong operational decisions or compliance exposure.
Packs must enforce measurement integrity (calibration, provenance) and reproducibility (parameter locks), while minimizing disclosure (e.g., sensitive location data).

## Cross-domain coherence (SC102 alignment note)
SC102 (core-only qualification) demonstrates that these invariants remain stable across D1–D9:

- authority envelope integrity
- policy/contract chain (baseline is hashable/pinnable)
- decision vocabulary stability (allow/deny/quarantine/rate_limit where defined)
- fail-closed behavior for forbidden effects
- evidence pack completeness and replayability
- minimal disclosure (only necessary information emitted)

Only domain semantics change (via Domain Packs), not the runtime grammar.

## Domain packs (canonical location)
Domain packs are defined under:
`catalog/domains/packs/<Dk>/<pack-id>/`

Each pack must declare:
- forbidden effects (domain semantics)
- expected reason codes
- required evidence fields and KPIs
- baselines (allow/deny/quarantine)
- safe vectors (stimuli) and expected outcomes