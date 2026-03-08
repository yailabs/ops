---
id: CATALOG-DOMAINS
title: Domains — Catalog Layer
status: draft
owner: catalog
effective_date: 2026-02-23
revision: 1
---

# Domains (Catalog)

This section defines the **macro-domain taxonomy** used by YAI to keep the platform coherent across fundamentally different problem spaces.

Domains here are **semantic domains** (what the problem is about), not software modules.  
They exist to prevent YAI from collapsing into a single vertical product and to ensure that the same runtime grammar can be demonstrated across different “worlds” (digital, physical, biological, etc.).

## What a domain is (D-Major)
A **D-Major** domain is a macro-area of reality where:
- events and outcomes have distinct meaning
- authority and constraints are expressed differently
- consequences (effects) carry different risks

D-Major taxonomy:

- **D1 — Digital** (compute/network/storage)
- **D2 — Physical** (cyber-physical, matter/energy)
- **D3 — Biological** (life, clinical/lab)
- **D4 — Social/Institutional** (people, regulation, procedures)
- **D5 — Economic** (value exchange, contracts)
- **D6 — Operational** (coordination, logistics, SRE/IR)
- **D7 — Cognitive/Cultural** (media, meaning, reputation)
- **D8 — Scientific** (measurement, reproducibility)
- **D9 — Environmental/Climatological** (earth systems, telemetry, hazards)

YAI does not “become” any of these domains. **YAI remains a governed runtime.**  
What changes is the domain semantics captured and tested by a **Domain Pack**.

## What remains invariant (runtime grammar)
Across all domains, YAI must preserve the same chain:

**trigger → context → authority/contract → decision → enforcement → evidence**

A domain changes:
- what an event means
- which effects are critical or forbidden
- what evidence is required to prove correct behavior

But the grammar above remains identical.

## Domain semantics vs runtime effect domains (important distinction)
- **D-Major domains** define semantics and validation criteria (this section).
- **Runtime effect domains** define where the runtime can produce or block effects:
  - control plane
  - network egress
  - storage writes
  - provider calls
  - resource access
  - artifact emission

A single D-Major domain may map to multiple runtime effect domains.

Example:
- An **Economic** workflow may involve:
  - provider calls (payments)
  - storage writes (ledger entries)
  - control workflows (approvals / separation of duties)

## How domains are used in catalog and qualification
- **Scenario specs (SC-xxx)** reference one or more D-Major domains.
- **Qualification tracks (QT-xxx)** execute scenarios using one or more domain packs.
- **Domain packs** encode domain semantics as operational contracts:
  - forbidden effects and allowlists
  - expected reason codes
  - required evidence fields
  - KPIs and thresholds
  - vectors and expected outcomes

## Files
- `D-MAJOR.md` — canonical D-Major taxonomy (definitions + IDs)
- `packs/` — domain packs (semantic packages) referenced by scenarios and qualification
- `trials/` — RealTarget trial specifications (procedures bound to packs; no runtime code)