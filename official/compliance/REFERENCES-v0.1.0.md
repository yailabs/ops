# REFERENCES (v0.1.0)

## Scope
This document lists authoritative external sources used for compliance posture and mappings, and defines how internal normative baselines are incorporated by reference into this repository.

## Audience
Procurement, legal/compliance, audit reviewers, and engineering stakeholders needing source traceability for posture claims and mappings.

## Policy (how to read and update references)
- External sources listed here are authoritative references only. This repository does not provide legal advice.
- Internal baselines (law) are the canonical operational interpretation and are incorporated by reference.
- Updates to references are versioned changes:
  - update `REFERENCES-vX.Y.Z.md` (new version)
  - update crosswalk/mapping docs accordingly
  - do not retroactively change released OFFICIAL baselines without a new release version

## External sources (authoritative)
The following sources are referenced by the compliance spine and may be activated depending on applicability (see `APPLICABILITY-MATRIX-v0.1.0.md`).

### Regulation (EU)
- EU AI Act (Reg. (EU) 2024/1689)
- GDPR (Reg. (EU) 2016/679)
- ePrivacy (Directive 2002/58/EC), where applicable
- CRA — Cyber Resilience Act (Reg. (EU) 2024/2847) (overlay)
- DORA (Reg. (EU) 2022/2554) (overlay)
- Data Act (Reg. (EU) 2023/2854) (overlay)
- Data Governance Act (Reg. (EU) 2022/868) (overlay)

### Directive (EU)
- NIS2 (Directive (EU) 2022/2555) (overlay)

### Standards and frameworks
- ISO/IEC 42001 — AI Management System (AIMS)
- ISO/IEC 23894 — AI risk management guidance
- ISO/IEC 27001 / 27002 — information security management and controls
- ISO/IEC 27017 / 27018 / 27701 — cloud and privacy extensions (overlay / customer-driven)
- NIST AI RMF 1.0 — AI risk management framework (mapping posture)
- NIST SSDF (SP 800-218) — secure software development framework
- SLSA — supply-chain integrity and provenance expectations

## Internal normative baseline (law) — incorporation by reference
This repository incorporates **law** by reference as the canonical internal baseline for:
- terminology and definitions
- contracts and invariants (runtime governance posture)
- compliance packs and schemas (e.g., GDPR packs, retention policy structures)
- templates and clauses used for pilots (where applicable)

### Why incorporation by reference
- Prevents drift between “what is defined” (law/contracts), “what is claimed” (OFFICIAL), and “what is proven” (EVIDENCE/WAVES).
- Enables pinned, reviewable baselines via commit SHA references in OFFICIAL Evidence Baseline blocks.

### Pointers (required)
Fill these pointers with the canonical locations in the law repository used by this release:

- law repository: `yai-labs/law` (canonical external repository)
- Terminology / glossary:
  - `law/foundation/terminology/*`
- Contracts and invariants:
  - `law/foundation/*` and `law/authority/*`
- Compliance packs and schemas:
  - `law/overlays/regulatory/*` and `law/overlays/sector/*`
- Formal bindings (if used):
  - `law/formal/` (bindings, traceability schema)

### Pinning rule (binding)
Any OFFICIAL document that relies on law MUST include the law pin SHA in its Evidence Baseline block. That pin is the authoritative internal baseline for interpretation.

## Related documents
- Applicability matrix: `/official/compliance/APPLICABILITY-MATRIX-v0.1.0.md`
- Conformity & evidence map: `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`
- AI Act crosswalk: `/official/compliance/AI-ACT-CROSSWALK-v0.1.0.md`
- Privacy posture: `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md`
- Security & supply chain posture: `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`