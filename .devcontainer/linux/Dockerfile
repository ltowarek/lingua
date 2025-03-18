FROM ubuntu:24.04

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    build-essential \
    ca-certificates \
    cmake \
    curl \
    git \
    libcurl4-openssl-dev \
    libedit-dev \
    libzstd-dev \
    llvm-dev \
    pkg-config \
    ninja-build \
    zip \
    zlib1g-dev

USER ubuntu

ENV VCPKG_ROOT="/home/ubuntu/vcpkg"
ENV PATH="$PATH:$VCPKG_ROOT"
RUN git clone https://github.com/microsoft/vcpkg.git $VCPKG_ROOT && \
    cd $VCPKG_ROOT && \
    ./bootstrap-vcpkg.sh -disableMetrics

ENV VCPKG_INSTALLED_DIR="$VCPKG_ROOT/installed"
COPY vcpkg.json /tmp/vcpkg.json
RUN cd /tmp && vcpkg install
