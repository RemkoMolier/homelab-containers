FROM alpine:3.17
LABEL maintainer="remko.molier@googlemail.com"

# Build arguments
ARG APPLICATION_VERSION="1.22.1"
ARG ALPINE_SUFFIX="r0"
ARG BUILD_DATE
ARG VCS_REF

# Labels
LABEL org.opencontainers.image.created=${BUILD_DATE}
LABEL org.opencontainers.image.authors="Remko Molier <remko.molier@googlemail.com>"
LABEL org.opencontainers.image.url="https://www.nginx.org/"
LABEL org.opencontainers.image.source="https://github.com/RemkoMolier/homelab-containers/nginx"
LABEL org.opencontainers.image.version="$APPLICATION_VERSION"
LABEL org.opencontainers.image.revision="$VCS_REF"
LABEL org.opencontainers.image.ref.name="ghcr.io/RemkoMolier/nginx"
LABEL org.opencontainers.image.title="nginx"
LABEL org.opencontainers.image.description="HTTP and reverse proxy server (stable version)"
LABEL org.opencontainers.image.documentation="https://github.com/RemkoMolier/homelab-containers/nginx/documentation.md"


# Build instructions
RUN apk update && \
    apk upgrade && \
    apk add --no-cache  nginx=$APPLICATION_VERSION-$ALPINE_SUFFIX && \
    rm -rf /var/www/localhost

# Provided volumes
VOLUME ["/etc/nginx","/run/nginx","/var/log/nginx","/var/www"]

# Container 
CMD ["/usr/sbin/nginx","-g","daemon off;"]
