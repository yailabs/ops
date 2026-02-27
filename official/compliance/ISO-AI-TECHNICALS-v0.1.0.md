# ISO AI TECHNICALS (v0.1.0)

## Scope
This document defines how ISO AI technical standards are used inside YAI Ops to stabilize terminology, architecture vocabulary, and data-quality language. It is not a compliance claim by itself; it is a vocabulary alignment policy.

## Audience
Technical writers, architects, and reviewers responsible for keeping OFFICIAL and CATALOG language consistent and non-ambiguous.

## Rules
1) OFFICIAL documents must use canonical terms from `/official/_glossary/TERMS-v0.1.0.md`.
2) Where industry-standard terminology is needed, ISO AI technical standards may be used as a reference vocabulary.
3) “Use” of these standards here means vocabulary alignment and definitions, not certification.

## ISO/IEC 22989 — AI concepts and terminology
### Intended use in this repo
- Align high-level AI terminology used in OFFICIAL documents.
- Reduce ambiguity in terms such as model/system, dataset, training/inference, validation, monitoring, etc.

### Where it applies
- `/official/_glossary/TERMS-v0.1.0.md` (canonical glossary)
- OFFICIAL: `/official/overview/`, `/official/tech-dossier/`, `/official/assurance/`
- CATALOG: scenario and domain descriptions where terms could be misread

### Output expectation
- Glossary entries that use consistent wording and avoid conflicting synonyms across documents.

## ISO/IEC 23053 — Framework for AI systems using machine learning
### Intended use in this repo
- Provide a stable architecture vocabulary for describing ML-centric systems:
  - components and interactions (data sources, models, pipelines, monitoring)
  - lifecycle stages and boundaries (development vs deployment vs operation)

### Where it applies
- `/official/tech-dossier/YAI-Technology-Dossier-v0.1.0.md`
- `/catalog/` (where ML components or workflows are described)

### Output expectation
- Architecture descriptions that remain consistent across versions and do not depend on product-specific terminology.

## ISO/IEC 5259-* — Data quality for analytics and ML
### Intended use in this repo
- Standardize vocabulary for data quality claims and metrics.
- Avoid vague claims about “good data” by mapping to data-quality dimensions.

### Where it applies
- `/official/assurance/` (when data quality is referenced)
- `/evidence/metrics/` (where captured) and `/evidence/reports/`
- `/catalog/scenarios/` (when data quality constraints are part of the scenario)

### Output expectation
- When data quality is claimed or measured, documents should reference explicit dimensions and, where possible, evidence-backed metrics.

## Notes
- This document supports consistent language across the YAI ecosystem. Compliance posture remains defined by:
  - `/official/compliance/APPLICABILITY-MATRIX-v0.1.0.md`
  - `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md`
  - and the relevant crosswalk/posture documents.