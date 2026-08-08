FROM node:24-bookworm

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ARG HTMLTEST_VERSION=0.17.0

ENV DEBIAN_FRONTEND=noninteractive \
    PNPM_HOME=/pnpm \
    PATH=/pnpm:$PATH \
    PUPPETEER_SKIP_DOWNLOAD=true

# System dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        awscli \
        ca-certificates \
        chromium \
        curl \
        git \
        jq \
        python3 \
        python3-pip \
        unzip \
        wget \
        yamllint \
    && rm -rf /var/lib/apt/lists/*

# Enable pnpm through Corepack
RUN corepack enable \
    && corepack prepare pnpm@latest --activate \
    && pnpm --version

# Install htmltest
RUN curl -fsSL \
        "https://github.com/wjdp/htmltest/releases/download/v${HTMLTEST_VERSION}/htmltest-linux-amd64-${HTMLTEST_VERSION}.tar.gz" \
        -o /tmp/htmltest.tar.gz \
    && tar -xzf /tmp/htmltest.tar.gz -C /tmp \
    && install -m 0755 /tmp/htmltest /usr/local/bin/htmltest \
    && rm -rf /tmp/htmltest /tmp/htmltest.tar.gz

# Python dependencies used by the CI checks
RUN python3 -m pip install --break-system-packages --no-cache-dir \
        yamllint

# Make Chromium discoverable by browser-based tools
ENV CHROME_BIN=/usr/bin/chromium \
    PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium

# Verify the toolchain during image build
RUN node --version \
    && pnpm --version \
    && python3 --version \
    && aws --version \
    && htmltest --version \
    && yamllint --version \
    && chromium --version

WORKDIR /build

CMD ["bash"]
