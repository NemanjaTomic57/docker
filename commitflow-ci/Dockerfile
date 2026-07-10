FROM golang:1.25-trixie

SHELL ["/bin/bash", "-o", "pipefail", "-e", "-c"]

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    build-essential=12.12 unzip=6.0-29 yamllint=1.37.1-1 \
  && rm -rf /var/lib/apt/lists/*

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
  && unzip awscliv2.zip \
  && ./aws/install

RUN curl -fsSL https://golangci-lint.run/install.sh | sh -s -- -b "$(go env GOPATH)/bin" v2.12.2

RUN curl -fsSL -o /tmp/hadolint \
    https://github.com/hadolint/hadolint/releases/download/v2.14.0/hadolint-linux-x86_64 \
  && chmod +x /tmp/hadolint \
  && mv /tmp/hadolint /usr/local/bin/hadolint

WORKDIR /workspace
