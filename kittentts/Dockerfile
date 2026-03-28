ARG BUILD_FROM
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

WORKDIR /usr/src
ENV PIP_BREAK_SYSTEM_PACKAGES=1

# Install system deps and Python packages
RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
        espeak-ng \
        git \
    \
    && pip3 install --no-cache-dir -U \
        setuptools \
        wheel \
    && pip3 install --no-cache-dir \
        "kittentts @ git+https://github.com/KittenML/KittenTTS.git@0.8.1" \
        "wyoming-kittentts @ git+https://github.com/tcarney/wyoming-kittentts.git@v0.2.0" \
    \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /
COPY rootfs /

# Persist model cache across restarts
ENV HF_HOME=/share/kittentts
