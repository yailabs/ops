# Publishing rules

## Scope
This document defines publication rules for runtime bundles, evidence bundles (waves), and OFFICIAL documents.

## Publication units
1) Runtime bundles (built/published from cli)
- Contain pinned versions of: yai (core), law (normative baseline), and other required dependencies/spec pins.
- Must include checksums and verification instructions (supply chain provenance expectations may be defined in `official/compliance/SECURITY-AND-SUPPLY-CHAIN-v0.1.0.md`).

2) Evidence bundles: WAVES (published from ops)
- Stored under `evidence/waves/` as immutable release bundles.
- A wave is valid for reference only if it contains:
  - `MANIFEST.json`
  - `INDEX.md`
  - `verify/` output (or equivalent verification artifacts)
  - `verify.sh` (or equivalent verification procedure) when applicable
- Waves may also be published as GitHub Releases (optional), but `evidence/waves/` is canonical.

3) OFFICIAL documents (published from ops)
- Stored under `official/` with explicit versioning.
- For each release, OFFICIAL content may be exported to PDF and attached to GitHub Releases (optional).

## Baseline requirements for OFFICIAL documents (mandatory)
Every OFFICIAL document MUST include an evidence baseline block specifying:
- Wave alias + wave_id
- Manifest hash (sha256)
- Policy hash (sha256) and index hash (sha256) when applicable
- Source pins:
  - yai commit sha
  - cli commit sha
  - law commit sha (or specs pin sha, if applicable)
- Verification pointer:
  - path to wave `verify/` outputs and the verification procedure reference

## Claims and evidence
- Any factual claim about behavior, containment, determinism, or security posture MUST reference:
  - the specific wave and run where it was measured or enforced
  - the policy/baseline used during that run
- Non-verified statements must be explicitly labeled and should not appear in OFFICIAL releases.

## Release hygiene
- Do not rewrite waves.
- Fixes and updates create new waves and/or new OFFICIAL versions.
- Keep `official/compliance/*` and `official/_glossary/*` consistent across releases.