FROM dhi.io/rust:1-debian13-sfw-dev AS builder

RUN apt-get update && \
    apt-get install -y --no-install-recommends git clang && \
    rm -rf /var/lib/apt/lists/* && \
    git config --global advice.detachedHead false

RUN git clone --depth=1 https://github.com/ZettaScaleLabs/ros-z.git

WORKDIR /build/ros-z
RUN cargo build --release -p ros-z-console
RUN cargo install --offline --path ros-z-console


FROM dhi.io/debian-base:trixie

COPY --from=builder /root/.cargo/ /usr/local/

RUN echo 'rosz:x:1000:' >> /etc/group && \
    echo 'rosz:x:1000:1000:rosz:/:/sbin/nologin' >> /etc/passwd

RUN mkdir -p /data && \
    chown rosz:rosz /data

VOLUME /data
WORKDIR /data

USER rosz:rosz

CMD ["ros-z-console"]
