ARG ARCH=
FROM ${ARCH}ubuntu:25.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ninja-build \
    python3 \
    python3-pip \
    python3-wheel \
    python3-setuptools \
    wget \
    lsb-release \
    software-properties-common \
    gnupg \
    pipx \
    cmake \
    git \
    unzip \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://dl.google.com/android/repository/android-ndk-r28b-linux.zip && \
    unzip -q android-ndk-r28b-linux.zip -d /opt && \
    rm android-ndk-r28b-linux.zip

ENV ANDROID_NDK_ROOT=/opt/android-ndk-r28b
ENV PATH="${ANDROID_NDK_ROOT}:${PATH}"

RUN pipx ensurepath && \
    pipx install conan

ENV DEBIAN_FRONTEND=

WORKDIR /workspace

CMD ["/bin/bash"]
