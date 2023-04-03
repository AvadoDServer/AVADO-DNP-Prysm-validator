ARG VERSION

FROM --platform=linux/amd64 gcr.io/prysmaticlabs/prysm/validator:${VERSION} as builder

FROM --platform=linux/amd64 debian:buster-slim

RUN apt update && \
    apt install -y \
    openssl \
    jq \
    && rm -rf /var/lib/apt/lists/*

COPY --from=builder /app/cmd/validator/validator /bin/validator

COPY files/start.sh /scripts/start.sh
RUN chmod +x /scripts/start.sh

ENTRYPOINT [ "/scripts/start.sh" ]

