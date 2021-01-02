FROM node:8-alpine3.11

# Set a timezone
ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY . .
RUN yarn install && yarn run build && apk add --no-cache curl

CMD node dist

HEALTHCHECK --interval=15s --timeout=30s --retries=50 \
  CMD curl -f localhost:8081/api || exit 1
