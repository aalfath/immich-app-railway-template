# Immich server (API + web UI + background workers) for Railway.
# Pinned by version and digest. Bump both together and add a CHANGELOG entry.
FROM ghcr.io/immich-app/immich-server:v3.4.1@sha256:7c489add298fc2f92cda4c777de6462aa206877e04087b815f62c7664af0b53b

# Fixed settings. Railway service variables override these.
ENV IMMICH_ENV=production \
    IMMICH_LOG_LEVEL=log \
    IMMICH_PORT=2283 \
    DB_PORT=5432 \
    REDIS_PORT=6379

EXPOSE 2283
ENTRYPOINT ["tini", "--", "/bin/bash", "-c"]
CMD ["start.sh"]
