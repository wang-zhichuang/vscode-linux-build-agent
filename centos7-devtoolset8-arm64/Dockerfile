FROM arm64v8/centos:centos7

ARG INSTALL_PKGS="devtoolset-8-gcc \
    devtoolset-8-gcc-c++ \
    devtoolset-8-gcc-gfortran \
    devtoolset-8-gdb \
    make \
    git \
    sudo \
    libsecret-devel \
    python3"

RUN yum install -y centos-release-scl-rh && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    yum install -y https://rpm.nodesource.com/pub_16.x/el/7/aarch64/nodejs-16.18.0-1nodesource.aarch64.rpm \
    rpm -V $INSTALL_PKGS && \
    yum -y clean all --enablerepo='*'

# update npm and install yarn
RUN npm install -g npm@latest
RUN npm install -g yarn

ENV PATH=/opt/rh/devtoolset-8/root/usr/bin/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

RUN mkdir -p /root/vscode
WORKDIR /root/vscode
