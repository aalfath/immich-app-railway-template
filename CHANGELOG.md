# Changelog

## 3.4.1 (2026-11-16)

- **Template now builds `Immich` and `Immich ML` from this repo** (`server/` and `machine-learning/`), so deployers get "update available" notices for new Immich versions. Earlier deploys ran the images directly and keep doing so until redeployed from the template.
- Immich v3.0.3 → **v3.4.1** (server and machine learning, pinned by digest). Immich runs its database migrations on start; back up Postgres and `/data` before upgrading an existing install. Release notes: https://github.com/immich-app/immich/releases/tag/v3.4.0 and https://github.com/immich-app/immich/releases/tag/v3.4.1
- Machine learning: `MACHINE_LEARNING_MODEL_REVISION=v2`, as in Immich's own compose file for v3.4.
- New deploys: Valkey 9 (was 8) and the Immich Postgres image pinned by digest. Dropped the unused `JWT_SECRET` variable.
