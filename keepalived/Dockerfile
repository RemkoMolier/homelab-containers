FROM alpine:3.17
LABEL maintainer="remko.molier@googlemail.com"

# Build arguments
ARG APPLICATION_VERSION="2.2.7"
ARG ALPINE_SUFFIX="r2"
ARG BUILD_DATE
ARG VCS_REF

# Labels
LABEL org.opencontainers.image.created=${BUILD_DATE}
LABEL org.opencontainers.image.authors="Remko Molier <remko.molier@googlemail.com>"
LABEL org.opencontainers.image.url="https://www.keepalived.org/"
LABEL org.opencontainers.image.source="https://github.com/RemkoMolier/homelab-containers/keepalived"
LABEL org.opencontainers.image.version="$APPLICATION_VERSION"
LABEL org.opencontainers.image.revision="$VCS_REF"
LABEL org.opencontainers.image.ref.name="ghcr.io/RemkoMolier/keepalived"
LABEL org.opencontainers.image.title="keepalived"
LABEL org.opencontainers.image.description="Health Checking for Linux Virtual Server & High-Availability"
LABEL org.opencontainers.image.documentation="https://github.com/RemkoMolier/homelab-containers/keepalived/documentation.md"


# Build instructions
RUN apk update && \
    apk upgrade && \
    apk add --no-cache  keepalived=$APPLICATION_VERSION-$ALPINE_SUFFIX 

# Provided volumes
VOLUME ["/etc/keepalived"]

# Container 
CMD ["/usr/sbin/keepalived","--dont-fork","--use-file","/etc/keepalived/keepalived.conf"]
