FROM rust:slim-bullseye as builder
RUN apt-get update
WORKDIR /darkforest-rs
COPY . .
RUN ls -ltra
RUN cargo install --path=mimc-fast --force

FROM debian:bullseye as app
RUN apt-get update
COPY --from=builder /usr/local/cargo/bin/mimc-fast /usr/local/bin/mimc-fast
ENV RUST_LOG=info
ENTRYPOINT ["mimc-fast"]