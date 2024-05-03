FROM node:21-alpine

# Add dependencies to get Bun working on Alpine
RUN apk --no-cache add ca-certificates wget bash unzip
# Install glibc to run Bun
RUN if [[ $(uname -m) == "aarch64" ]] ; \
    then \
    # aarch64
    wget https://raw.githubusercontent.com/squishyu/alpine-pkg-glibc-aarch64-bin/master/glibc-2.26-r1.apk ; \
    apk add --no-cache --allow-untrusted --force-overwrite glibc-2.26-r1.apk ; \
    rm glibc-2.26-r1.apk ; \
    else \
    # x86_64
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk ; \
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub ; \
    apk add --no-cache --force-overwrite glibc-2.28-r0.apk ; \
    rm glibc-2.28-r0.apk ; \
    fi
# Install Bun in the specified version
RUN npm install bun --global

# Install Git
RUN apk --no-cache add git

# Install Turborepo
RUN npm install turbo --global

# Install Supabase-CLI
RUN if [[ $(uname -m) == "aarch64" ]] ; \
    then \
    # aarch64
    wget https://github.com/supabase/cli/releases/download/v1.166.0/supabase_1.166.0_linux_arm64.apk ; \
    apk add --no-cache --allow-untrusted --force-overwrite supabase_1.166.0_linux_arm64.apk ; \
    rm supabase_1.166.0_linux_arm64.apk ; \
    else \
    # x86_64
    wget https://github.com/supabase/cli/releases/download/v1.166.0/supabase_1.166.0_linux_amd64.apk ; \
    apk add --no-cache --force-overwrite supabase_1.166.0_linux_amd64.apk ; \
    rm supabase_1.166.0_linux_amd64.apk ; \
    fi
