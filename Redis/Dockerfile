FROM redis:6.0.9-alpine

RUN apk add --update curl && \
    rm -rf /var/cache/apk/*

COPY redis.conf /usr/local/etc/redis/redis.conf

CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]

HEALTHCHECK --interval=15s --timeout=30s --retries=50 \
  CMD curl -f localhost:6379 || exit 1
