FROM nginx:stable-alpine

RUN apk update && apk add --no-cache curl

# Set a timezone
ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY default /etc/nginx/conf.d/default.conf
COPY dist /usr/share/nginx/html

CMD echo $api > /usr/share/nginx/html/apiUrl.txt && nginx -g "daemon off;"

HEALTHCHECK --interval=15s --timeout=30s --retries=50 \
  CMD curl -f localhost:80 || exit 1
