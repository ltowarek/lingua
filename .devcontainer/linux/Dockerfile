FROM ubuntu:24.04

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    ca-certificates \
    clang \
    cmake \
    libcurl4-openssl-dev \
    git \
    libedit-dev \
    libzstd-dev \
    llvm-dev \
    ninja-build \
    zlib1g-dev
