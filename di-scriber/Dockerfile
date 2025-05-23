FROM bitnami/git AS clone

WORKDIR /app
RUN git clone https://github.com/noma-t/Di-Scriber.git

FROM rust AS builder

WORKDIR /app

COPY --from=clone /app/* /app/

RUN cargo build --release && chmod +x /app/target/release/Di-Scriber


FROM ubuntu

WORKDIR /app
COPY --from=builder /app/target/release/Di-Scriber /app/
COPY ./config.toml /app/

ENV DISCORD_BOT_TOKEN=""

CMD ["/app/Di-Scriber"]
