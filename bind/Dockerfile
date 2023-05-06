FROM alpine:3.17
LABEL maintainer="remko.molier@googlemail.com"

# Build arguments
ARG APPLICATION_VERSION
ARG ALPINE_SUFFIX="r0"
ARG BUILD_DATE
ARG VCS_REF

# Labels
LABEL org.opencontainers.image.created=${BUILD_DATE}
LABEL org.opencontainers.image.authors="Remko Molier <remko.molier@googlemail.com>"
LABEL org.opencontainers.image.url="https://www.isc.org/"
LABEL org.opencontainers.image.source="https://github.com/RemkoMolier/homelab-containers/bind"
LABEL org.opencontainers.image.version="$APPLICATION_VERSION"
LABEL org.opencontainers.image.revision="$VCS_REF"
LABEL org.opencontainers.image.ref.name="ghcr.io/RemkoMolier/bind"
LABEL org.opencontainers.image.title="ISC BIND DNS"
LABEL org.opencontainers.image.description="The ISC DNS server"
LABEL org.opencontainers.image.documentation="https://github.com/RemkoMolier/homelab-containers/bind/documentation.md"


# Build instructions
RUN apk update && \
    apk upgrade && \
    apk add --no-cache  bind=$APPLICATION_VERSION-$ALPINE_SUFFIX \
                        bind-dnssec-tools=$APPLICATION_VERSION-$ALPINE_SUFFIX 

# Exposed ports
EXPOSE 53/tcp 53/udp 953/tcp

# Provided volumes
VOLUME ["/etc/bind", "/var/bind"]

# Container 
CMD ["/usr/sbin/named", "-c", "/etc/bind/named.conf", "-f", "-g", "-u", "named"]
