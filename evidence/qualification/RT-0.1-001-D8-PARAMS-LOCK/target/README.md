# D8 Target

Black-box publish target for D8 is the artifact store volume served by nginx.

## Docker target (L1)
- Compose file: `docs/40-qualification/_shared/d8-artifact-store/docker-compose.yml`
- Store path: `docs/40-qualification/_shared/d8-artifact-store/_artifact_store`
- Public URL base: `http://127.0.0.1:18080/`

The `workload` container has no writable mount to `_artifact_store`.
Only `runtime` has `rw` mount and can publish artifacts.

## Local target (L0)
- Store path: `docs/40-qualification/RT-0.1-001-D8-PARAMS-LOCK/target/_artifact_store`
