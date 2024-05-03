ARG NODE_VERSION=21

FROM node:${NODE_VERSION}-slim as base

ARG BUN_VERSION=1.1.6

WORKDIR /build

# Install Bun in the specified version
RUN apt update && apt install -y bash curl unzip && \
 curl -fsSL https://bun.sh/install | bash -s -- bun-v${BUN_VERSION}

ENV PATH="${PATH}:/root/.bun/bin"

# adding apk deps to avoid node-gyp related errors and some other stuff. adds turborepo globally
RUN apk add -f --update --no-cache --virtual .gyp nano bash libc6-compat python3 make g++ \
      && yarn global add turbo \
      && apk del .gyp

# Copy the lock file and app manifest, then install
# the dependencies, including the dev dependencies
#
COPY bun.lockb package.json ./
