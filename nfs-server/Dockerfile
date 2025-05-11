
FROM debian:12.10

ENV NFS_VERSION 1:1.3.4-6

ENV C2D_RELEASE 1.3.4

RUN set -x && \
    apt-get update && apt-get install -qq -y openssl nfs-kernel-server=${NFS_VERSION}* && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir /exports

COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +rx /usr/local/bin/docker-entrypoint.sh

VOLUME /exports

EXPOSE 2049/tcp
EXPOSE 20048/tcp

ENTRYPOINT ["/usr/local/bin/docker-entrypoint.sh"]
CMD ["/exports"]
