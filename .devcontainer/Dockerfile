# CodeSandbox supports debian & ubuntu based images
FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# Example; install htop by default
# RUN apt update -y && apt install -y htop

RUN apt-get update && \
    apt-get install -y \
        ca-certificates \
        nodejs \
        npm \
        wget && \
    update-ca-certificates

ARG HUGO_VERSION="0.131.0"
RUN wget --quiet "https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz" && \
    tar xzf hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && \
    rm -r hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && \
    mv hugo /usr/bin && \
    chmod 755 /usr/bin/hugo

# The project will be mounted in /workspace by default

WORKDIR /src
COPY ./ /src

# Every new shell will open inside the built container

# On top of this build, we install `zsh`, `git` and `docker` as additional
# Docker layers.
