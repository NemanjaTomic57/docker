FROM node:24-bookworm

RUN apt-get update && \
  apt-get install -y --no-install-recommends \
  bash ca-certificates unzip curl python3 yamllint \
  chromium \
  libasound2 \
  libatk-bridge2.0-0 \
  libatk1.0-0 \
  libatspi2.0-0 \
  libc6 \
  libcairo2 \
  libcups2 \
  libdbus-1-3 \
  libdrm2 \
  libexpat1 \
  libgbm1 \
  libglib2.0-0 \
  libnspr4 \
  libnss3 \
  libpango-1.0-0 \
  libpangocairo-1.0-0 \
  libstdc++6 \
  libudev1 \
  libuuid1 \
  libx11-6 \
  libx11-xcb1 \
  libxcb-dri3-0 \
  libxcb1 \
  libxcomposite1 \
  libxcursor1 \
  libxdamage1 \
  libxext6 \
  libxfixes3 \
  libxi6 \
  libxkbcommon0 \
  libxrandr2 \
  libxrender1 \
  libxshmfence1 \
  libxss1 \
  libxtst6 \
  && rm -rf /var/lib/apt/lists/*

RUN npm install --global corepack@latest \
  corepack enable pnpm \
  corepack use pnpm@latest-11

RUN curl -fsSL https://awscli.amazonaws.com/v2/install.sh | bash -s -- --system

RUN curl https://htmltest.wjdp.uk | bash -s -- -b /usr/local/bin

RUN pnpm --version \
    && node --version \
    && aws --version \
    && yamllint --version \
    # && htmltest --version \
    && python3 --version
