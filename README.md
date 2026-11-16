[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/new/template/immich-2?utm_medium=integration&utm_source=button&utm_campaign=immich)

# Immich on Railway

Railway template for [Immich](https://immich.app), the self-hosted photo and video backup app. Template: https://railway.com/deploy/immich-2 · Repo: https://github.com/aalfath/immich-app-railway-template

It deploys **Immich v3.4.1** as four services:

| Service | Source | Network | Volume |
| --- | --- | --- | --- |
| `Immich` | this repo, `server/` (`ghcr.io/immich-app/immich-server:v3.4.1`, pinned by digest) | public, port 2283, health check `/api/server/ping` | `/data` (photos, videos, thumbnails) |
| `Immich ML` | this repo, `machine-learning/` (`ghcr.io/immich-app/immich-machine-learning:v3.4.1`, pinned by digest) | private, port 3003, health check `/ping` | `/cache` (models) |
| `Postgres` | `ghcr.io/immich-app/postgres:14-vectorchord0.4.3-pgvectors0.2.0` (pinned by digest) | private, port 5432 | `/var/lib/postgresql/data` |
| `Redis` | `valkey/valkey:9` (pinned by digest) | private, port 6379 | `/data` |

The images and digests are the ones in Immich's own `docker-compose.yml` for v3.4.1.

## Variables

Nothing to fill in. The template sets:

- `Immich`: `DB_HOSTNAME`, `DB_USERNAME`, `DB_PASSWORD`, `DB_DATABASE_NAME` (references to `Postgres`), `REDIS_HOSTNAME` (reference to `Redis`), `IMMICH_MACHINE_LEARNING_URL` (private URL of `Immich ML`), `PORT=2283`.
- `Immich ML`: `PORT=3003`.
- `Postgres`: `POSTGRES_USER=immich`, `POSTGRES_DB=immich`, a generated `POSTGRES_PASSWORD`, `PGDATA` below the volume mount, `POSTGRES_INITDB_ARGS=--data-checksums`, `DB_STORAGE_TYPE=SSD`.

Fixed settings (`IMMICH_ENV`, `IMMICH_LOG_LEVEL`, `IMMICH_PORT`, `DB_PORT`, `REDIS_PORT`, the ML cache folder and model revision) are baked into the Dockerfiles; a Railway variable with the same name overrides them. Optional settings (`TZ`, SMTP, OAuth, storage template) are set in Immich's admin settings or as extra variables, see [Immich's environment variables](https://docs.immich.app/install/environment-variables).

The first user who opens the public URL creates the admin account, so open it right after deploying.

## Updates

`Immich` and `Immich ML` build from this repo. When a new Immich version is merged to `main`, Railway shows deployers an "update available" notice, and they choose when to apply it. Read [CHANGELOG.md](CHANGELOG.md) and Immich's release notes first, and back up your database and `/data` volume before a major upgrade. `Postgres` and `Redis` run pinned images and are not updated by the template.

## Backups

Immich's automatic database dumps (in `/data/backups`) hold metadata only. Back up the whole `/data` volume and the Postgres volume, and don't keep Immich as the only copy of your photos.
