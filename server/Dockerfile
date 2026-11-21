# Immich server (API + web UI + background workers) for Railway.
# Pinned by version and digest. Bump both together and add a CHANGELOG entry.
FROM ghcr.io/immich-app/immich-server:v3.4.2@sha256:fc880c1bf665b4aab1e74c15e56ab871225989cd546536e6b77e771869af06bd

# Fixed settings. Railway service variables override these.
ENV IMMICH_ENV=production \
    IMMICH_LOG_LEVEL=log \
    IMMICH_PORT=2283 \
    DB_PORT=5432 \
    REDIS_PORT=6379

EXPOSE 2283
ENTRYPOINT ["tini", "--", "/bin/bash", "-c"]
CMD ["start.sh"]
