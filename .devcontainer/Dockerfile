ARG NODE_VERSION=20

FROM node:${NODE_VERSION}-slim as build

ARG BUN_VERSION=1.0.15

WORKDIR /build

# Install Bun in the specified version
RUN apt update && apt install -y bash curl unzip && \
 curl https://bun.sh/install | bash -s -- bun-v${BUN_VERSION}

ENV PATH="${PATH}:/root/.bun/bin"

#
# Copy the lock file and app manifest, then install
# the dependencies, including the dev dependencies
#
COPY bun.lockb package.json ./
