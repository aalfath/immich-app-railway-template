# Immich machine learning (smart search, faces, OCR) for Railway. Private service.
# Pinned by version and digest. Keep it on the same version as ../server.
FROM ghcr.io/immich-app/immich-machine-learning:v3.4.2@sha256:739405742a79bd7447227c553bb62ed5491aa36acf00bc667af7f9c93b6fae91

# Fixed settings. Railway service variables override these.
# MACHINE_LEARNING_MODEL_REVISION=v2 matches Immich's own docker-compose.yml since v3.4.
ENV IMMICH_ENV=production \
    IMMICH_LOG_LEVEL=log \
    IMMICH_PORT=3003 \
    MACHINE_LEARNING_CACHE_FOLDER=/cache \
    MACHINE_LEARNING_MODEL_REVISION=v2

EXPOSE 3003
