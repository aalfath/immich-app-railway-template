# Changelog

## 3.4.2 (2026-11-21)

- No breaking changes. Photos and videos on the `/data` volume, the database and the model cache are kept. Back up Postgres and `/data` before any Immich upgrade, as upstream advises.
- Immich [v3.4.2](https://github.com/immich-app/immich/releases/tag/v3.4.2): bug fixes (web CSP for external styles, integrity report downloads, the Prometheus exporter listener, VAAPI transcoding) and a new FUTO Backups version.
- Server: `ghcr.io/immich-app/immich-server:v3.4.2@sha256:fc880c1bf665b4aab1e74c15e56ab871225989cd546536e6b77e771869af06bd`.
- Machine learning: `ghcr.io/immich-app/immich-machine-learning:v3.4.2@sha256:739405742a79bd7447227c553bb62ed5491aa36acf00bc667af7f9c93b6fae91`.

## 3.4.1 (2026-11-16)

- **Template now builds `Immich` and `Immich ML` from this repo** (`server/` and `machine-learning/`), so deployers get "update available" notices for new Immich versions. Earlier deploys ran the images directly and keep doing so until redeployed from the template.
- Immich v3.0.3 → **v3.4.1** (server and machine learning, pinned by digest). Immich runs its database migrations on start; back up Postgres and `/data` before upgrading an existing install. Release notes: https://github.com/immich-app/immich/releases/tag/v3.4.0 and https://github.com/immich-app/immich/releases/tag/v3.4.1
- Machine learning: `MACHINE_LEARNING_MODEL_REVISION=v2`, as in Immich's own compose file for v3.4.
- New deploys: Valkey 9 (was 8) and the Immich Postgres image pinned by digest. Dropped the unused `JWT_SECRET` variable.
