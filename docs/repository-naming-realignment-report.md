# Repository Naming Realignment Report (`ops`)

Date: 2026-03-08

## Scope
Realignment of repository naming references after the rename wave already completed on GitHub/local/remotes.

Applied mapping in this repo:
- `yai-labs/yai-ops` -> `yai-labs/ops`
- `yai-labs/yai-law` -> `yai-labs/law`
- `yai-labs/yai-sdk` -> `yai-labs/sdk`
- `yai-labs/yai-cli` -> `yai-labs/cli`
- `yai-labs/yai-infra` -> `yai-labs/infra`
- `yai-labs/yai-studio` -> `yai-labs/studio`

Repository identity text updated where appropriate:
- `yai-ops` -> `ops`
- `yai-law` -> `law`
- `yai-sdk` -> `sdk`
- `yai-cli` -> `cli`
- `yai-infra` -> `infra`
- `yai-studio` -> `studio`

## Main areas updated
- `README.md`
- governance/tracking top-level docs (`GOVERNANCE.md`, `PUBLISHING-RULES.md`, `TRACKING-HARDENING.md`)
- operational/publication material under `official/**`
- catalog and collateral docs (`catalog/**`, `collateral/**`)
- active qualification scripts/docs under `evidence/qualification/**`
- validation/proof/readme references under `evidence/validation/**`

## Legacy/path decision
- No dependency path refactor was required in `ops` (no active `deps/*` tree to rename).
- Legacy naming was realigned at repository identity / URL / documentation level.

## Intentional residual legacy kept
- Historical release and evidence artifacts were kept unchanged when they encode historical provenance:
  - `official/_releases/RELEASE-2026-02-26-v0.1.0/bundle_refs.txt`
  - `evidence/qualification/DEMO/**/artifacts/cli/01-yai-version.txt`
- These are historical records, not current repository identity guidance.

## Impact summary
- Cross-repo references now point to current GitHub repository names.
- README and publication-facing current docs no longer present old repo names as active identities.
- Product branding (e.g., “YAI Ops”) was not mass-rewritten; realignment was limited to repository naming context.
