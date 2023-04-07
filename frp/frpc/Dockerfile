FROM debian:bullseye-slim

ARG FRP_VERSION=0.47.0
ARG TARGET=frpc

RUN set -x; buildDeps='wget' \
    && apt-get update \ 
    && apt-get install -y $buildDeps \
    && wget -c https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && tar -xvpzf frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && cp frp_${FRP_VERSION}_linux_amd64/${TARGET} /usr/bin/frpx \
    && chmod +x /usr/bin/frpx \
    && rm -rf frp_${FRP_VERSION}_linux_amd64 \
    && rm -rf frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && apt-get purge -y --auto-remove $buildDeps \
    && mkdir -p /etc/frp

VOLUME /etc/frp

CMD frpx -c /etc/frp/conf.ini