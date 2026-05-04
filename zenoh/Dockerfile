FROM dhi.io/debian-base:trixie-dev

ARG ZENOH_VERSION

COPY zenoh-public-key.gpg /etc/apt/keyrings/
COPY zenoh.sources /etc/apt/sources.list.d/

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        catatonit \
        zenoh=${ZENOH_VERSION} \
        zenoh-backend-filesystem=${ZENOH_VERSION} \
        zenoh-backend-influxdb-v2=${ZENOH_VERSION} \
        zenoh-backend-rocksdb=${ZENOH_VERSION} \
        zenoh-backend-s3=${ZENOH_VERSION} \
        zenoh-plugin-mqtt=${ZENOH_VERSION} \
        zenoh-plugin-remote-api=${ZENOH_VERSION} \
        zenoh-plugin-webserver=${ZENOH_VERSION} && \
    rm -rf /var/lib/apt/lists/*

RUN echo 'zenoh:x:1000:' >> /etc/group && \
    echo 'zenoh:x:1000:1000:zenoh:/:/sbin/nologin' >> /etc/passwd

ENV ZENOH_HOME=/var/lib/zenoh

RUN mkdir -p ${ZENOH_HOME} && \
    chown zenoh:zenoh ${ZENOH_HOME}

VOLUME ${ZENOH_HOME}

USER zenoh:zenoh

ENTRYPOINT ["catatonit", "--"]
CMD ["zenohd"]
