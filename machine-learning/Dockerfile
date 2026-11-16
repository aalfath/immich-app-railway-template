# Immich machine learning (smart search, faces, OCR) for Railway. Private service.
# Pinned by version and digest. Keep it on the same version as ../server.
FROM ghcr.io/immich-app/immich-machine-learning:v3.4.1@sha256:8adebf414256f6e4f837bfbb66fa94f14f4da7260e3a1d65cbba49e4e35d8764

# Fixed settings. Railway service variables override these.
# MACHINE_LEARNING_MODEL_REVISION=v2 matches Immich's own docker-compose.yml since v3.4.
ENV IMMICH_ENV=production \
    IMMICH_LOG_LEVEL=log \
    IMMICH_PORT=3003 \
    MACHINE_LEARNING_CACHE_FOLDER=/cache \
    MACHINE_LEARNING_MODEL_REVISION=v2

EXPOSE 3003
