FROM dhi.io/rust:1-debian13-sfw-dev AS builder

RUN apt-get update && \
    apt-get install -y --no-install-recommends git clang && \
    rm -rf /var/lib/apt/lists/* && \
    git config --global advice.detachedHead false

WORKDIR /build
RUN git clone --depth=1 https://github.com/ZettaScaleLabs/hiroz.git

WORKDIR /build/hiroz/crates
RUN cargo install --path hiroz-union


FROM dhi.io/debian-base:trixie-dev

COPY --from=builder /root/.cargo/bin/hu /usr/local/bin/hu

RUN echo 'hiroz:x:1000:' >> /etc/group && \
    echo 'hiroz:x:1000:1000:hiroz:/:/sbin/nologin' >> /etc/passwd

RUN mkdir -p /data && \
    chown hiroz:hiroz /data

VOLUME /data
WORKDIR /data

USER hiroz:hiroz

CMD ["hu"]
