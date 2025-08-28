FROM        --platform=$TARGETOS/$TARGETARCH ghcr.io/graalvm/jdk-community:24

LABEL       author="Giovanni Palma" maintainer="nannipa02@gmail.com"

LABEL       org.opencontainers.image.licenses=MIT

FROM        --platform=$TARGETOS/$TARGETARCH ghcr.io/graalvm/jdk-community:24

LABEL       author="Giovanni Palma" maintainer="nannipa02@gmail.com"

LABEL       org.opencontainers.image.licenses=MIT

RUN         microdnf install -y \
                curl \
                lsof \
                ca-certificates \
                openssl \
                git \
                tar \
                sqlite \
                fontconfig \
                tzdata \
                iproute \
                freetype \
                tini \
                zip \
                unzip \
                jq \
            && microdnf clean all

## Setup user and working directory
RUN         useradd -m -d /home/container -s /bin/bash container
USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]

## Setup user and working directory
RUN         useradd -m -d /home/container -s /bin/bash container
USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
