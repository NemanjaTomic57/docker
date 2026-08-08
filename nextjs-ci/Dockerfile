FROM node:24-bookworm

RUN apt-get update && \
  apt-get install -y --no-install-recommends \
  bash ca-certificates unzip curl python3 yamllint

RUN npm install --global corepack@latest \
  corepack enable pnpm \
  corepack use pnpm@latest-11

RUN curl -fsSL https://awscli.amazonaws.com/v2/install.sh | bash -s -- --system

# RUN curl https://htmltest.wjdp.uk | sudo bash -s -- -b /usr/local/bin

RUN pnpm --version \
    && node --version \
    && aws --version \
    && yamllint --version \
    # && htmltest --version \
    && python3 --version
