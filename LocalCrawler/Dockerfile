FROM node:8-alpine3.11

# Set a timezone
ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY . .
RUN yarn install && yarn upgrade chokidar && yarn run build && apk add --no-cache curl

CMD node --max-old-space-size=8096 dist

HEALTHCHECK --interval=15s --timeout=30s --retries=50 \
  CMD curl -f localhost:8082/api/ || exit 1
