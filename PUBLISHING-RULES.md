# Publishing rules

- Runtime bundles: published from `yai-cli` (includes pinned yai + pinned yai-law + checksums + verify)
- Evidence bundles (waves): published from `yai-ops` under `evidence/waves/` and GitHub Releases
- Official docs: published from `yai-ops/official/` and exported to PDF per release

Every official doc must carry:
- Wave alias + wave_id
- Manifest sha256 + policy hash (+ index sha256 if applicable)
- yai sha + yai-cli sha + yai-law sha (or specs pin sha)
