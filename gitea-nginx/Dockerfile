ARG BUILD_DATE
ARG VERSION=v1.12.1
ARG REVISION

#FROM gitea/gitea:$VERSION as gitea
FROM node:alpine as gitea

RUN apk add --no-cache \
    git \
    make

ARG VERSION
ENV VERSION $VERSION
RUN git clone --depth=1 --branch="$VERSION" https://github.com/go-gitea/gitea.git /gitea

WORKDIR /gitea/
RUN make webpack

#--------------#

FROM nginx:alpine

LABEL maintainer="Sandro Jäckel <sandro.jaeckel@gmail.com>" \
  org.opencontainers.image.created=$BUILD_DATE \
  org.opencontainers.image.authors="Sandro Jäckel <sandro.jaeckel@gmail.com>" \
  org.opencontainers.image.url="https://github.com/SuperSandro2000/docker-images/tree/gitea/gitea-nginx" \
  org.opencontainers.image.documentation="https://github.com/go-gitea/gitea" \
  org.opencontainers.image.source="https://github.com/SuperSandro2000/docker-images" \
  org.opencontainers.image.version=$VERSION \
  org.opencontainers.image.revision=$REVISION \
  org.opencontainers.image.vendor="SuperSandro2000" \
  org.opencontainers.image.licenses="MIT" \
  org.opencontainers.image.title="Gitea Nginx" \
  org.opencontainers.image.description="Git with a cup of tea, painless self-hosted git service"

COPY --from=gitea [ "/gitea/public", "/gitea/public" ]
COPY [ "files/default.template", "/etc/nginx/conf.d/default.template" ]

WORKDIR /etc/nginx/
CMD [ "ash", "-c", "envsubst '${GITEA_SERVER},${NGINX_DOMAIN}' < /etc/nginx/conf.d/default.template > /etc/nginx/conf.d/default.conf && exec nginx-debug -g 'daemon off;'" ]
