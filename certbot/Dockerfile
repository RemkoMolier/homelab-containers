FROM alpine:3.18
LABEL maintainer="remko.molier@googlemail.com"

# Build arguments
ARG APPLICATION_VERSION="1.32.0"
ARG ALPINE_SUFFIX="r0"
ARG BUILD_DATE
ARG VCS_REF

# Labels
LABEL org.opencontainers.image.created=${BUILD_DATE}
LABEL org.opencontainers.image.authors="Remko Molier <remko.molier@googlemail.com>"
LABEL org.opencontainers.image.url="https://github.com/certbot/certbot"
LABEL org.opencontainers.image.source="https://github.com/RemkoMolier/homelab-containers/certbot"
LABEL org.opencontainers.image.version="$APPLICATION_VERSION"
LABEL org.opencontainers.image.revision="$VCS_REF"
LABEL org.opencontainers.image.ref.name="ghcr.io/RemkoMolier/certbot"
LABEL org.opencontainers.image.title="certbot"
LABEL org.opencontainers.image.description="An ACME client that can update Apache/Nginx configurations"
LABEL org.opencontainers.image.documentation="https://github.com/RemkoMolier/homelab-containers/certbot/documentation.md"


# Build instructions
RUN apk update && \
    apk upgrade && \
    apk add --no-cache  certbot=$APPLICATION_VERSION-$ALPINE_SUFFIX 

# Provided volumes
VOLUME ["/etc/letsencrypt", "/var/lib/letsencrypt","/var/log/letsencrypt"]

# Container 
ENTRYPOINT ["/usr/bin/certbot"]
