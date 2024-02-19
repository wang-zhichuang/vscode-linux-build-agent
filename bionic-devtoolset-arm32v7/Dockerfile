FROM arm32v7/ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive
ARG NODE_VERSION="16.20.2"

RUN apt-get update && apt-get install -y --no-install-recommends \
  software-properties-common \
  gcc \
  g++ \
  binutils \
  build-essential \
  git \
  pkg-config \
  sudo \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg \
  make \
  python3 \
  libkrb5-dev \
  unzip \
  jq

# Set python3 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 1
RUN python --version

# setup nodejs repo
RUN curl -L -O https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-armv7l.tar.gz && \
    tar -xzf node-v${NODE_VERSION}-linux-armv7l.tar.gz && \
    cp -R node-v${NODE_VERSION}-linux-armv7l/* /usr/local/ && \
    rm -rf node-v${NODE_VERSION}-linux-armv7l* && \
    node --version && \
    npm install -g yarn

RUN mkdir -p /root/vscode
WORKDIR /root/vscode
