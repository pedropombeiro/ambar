FROM rabbitmq:3.6-management-alpine

RUN apk update && apk add --no-cache curl

# Set a timezone
ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY rabbitmq.conf /etc/rabbitmq/rabbitmq.conf
RUN chmod 777 /etc/rabbitmq/rabbitmq.conf

HEALTHCHECK --interval=15s --timeout=30s --retries=50 \
  CMD curl -f localhost:15672 || exit 1


