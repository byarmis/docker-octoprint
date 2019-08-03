FROM haproxy
LABEL maintainer="ben@yarm.is"

RUN groupadd haproxy \
 && useradd -g haproxy haproxy

USER haproxy
#COPY haproxy.cfg.original /usr/local/etc/haproxy/haproxy.cfg
COPY haproxy.cfg /usr/local/etc/haproxy/haproxy.cfg
USER root

