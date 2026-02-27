# APPLICABILITY MATRIX (v0.1.0)

## Scope
This matrix declares what is treated as CORE vs OVERLAY for YAI Ops compliance posture, and which triggers enable overlays. It is used to keep OFFICIAL claims bounded and to prevent “accidental compliance promises”.

## Audience
Procurement, legal/compliance, security reviewers, and auditors determining which regulatory and standards mappings apply to a specific pilot/deployment.

## Definitions
- **CORE**: always-on posture and mapping used for YAI’s baseline documentation and evidence discipline.
- **OVERLAY**: additional requirements activated only when a specific trigger is met (sector, distribution model, data-sharing posture, etc.).
- **Trigger**: an objective condition that activates an overlay.
- **Evidence anchor**: the canonical document(s) in this repo where requirements are mapped to artifacts and evidence.

## Rules
1) Applicability must be declared for each pilot instance (SOW / delivery notes).
2) OFFICIAL documents reference CORE by default; OVERLAYS are referenced only when triggers are satisfied.
3) “Applicable” does not mean “certified” — it means “mapped to controls and evidence anchors in this repository.”

## Matrix
| Item | Type | Trigger | Applies when | Evidence anchor |
|---|---|---|---|---|
| EU AI Act (Reg. (EU) 2024/1689) | CORE | EU placement/use context | System is placed on the market / put into service / used within EU context | `/official/compliance/AI-ACT-CROSSWALK-v0.1.0.md` |
| GDPR (Reg. (EU) 2016/679) | CORE | Personal data processed | Logs/prompts/telemetry/support artifacts include personal data | `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md` |
| ePrivacy (Dir. 2002/58/EC) | CORE* | Communications context | Communications metadata/identifiers regulated by ePrivacy are processed (as applicable) | `/official/compliance/PRIVACY-GDPR-ePRIVACY-v0.1.0.md` |
| ISO/IEC 42001 (AIMS) | CORE | Target posture | Management-system posture adopted for AI governance program | `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md` |
| ISO/IEC 23894 | CORE | Risk posture | AI risk management guidance used for controls and reporting | `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md` |
| NIST AI RMF 1.0 | CORE | Mapping posture | Customer/audit mapping baseline for risk functions | `/official/compliance/CONFORMITY-EVIDENCE-MAP-v0.1.0.md` |
| ISO/IEC 27001/27002 | CORE | Security baseline | Procurement baseline requiring structured security controls and auditability | `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md` |
| NIST SSDF (SP 800-218) + SLSA | CORE | Supply-chain posture | CI/CD and releases require development controls and provenance expectations | `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md` |
| CRA (Reg. (EU) 2024/2847) | OVERLAY | Product distribution | YAI is distributed as a product/software with digital elements in CRA scope | `/official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md` |
| NIS2 (Dir. (EU) 2022/2555) | OVERLAY | Sector | Customer is an essential/important entity or supply chain falls under NIS2 expectations | `/official/compliance/SECTOR-OVERLAYS-v0.1.0.md` |
| DORA (Reg. (EU) 2022/2554) | OVERLAY | Finance | Customer is in financial sector or engagement is as ICT third-party provider | `/official/compliance/SECTOR-OVERLAYS-v0.1.0.md` |
| Data Act + Data Governance Act | OVERLAY | Data sharing/intermediation | Use case involves regulated data sharing, intermediation, or marketplace-like posture | `/official/compliance/SECTOR-OVERLAYS-v0.1.0.md` |

\* ePrivacy applicability depends on the concrete communications context and applicable national implementations where relevant.

## Pilot instance applicability declaration (template)
For each pilot instance, record:
- Declared CORE: (AI Act, GDPR, ISO/NIST mappings, security baseline)
- Activated OVERLAYS: (CRA / NIS2 / DORA / Data Act+DGA) with triggers
- Evidence wave anchor: `<wave alias + wave id + hashes>` (see pilot delivery spec)

Reference:
- Pilot delivery spec: `/official/delivery/YAI-Pilot-Delivery-Spec-v0.1.0.md`