FROM ghcr.io/kumanoryo/debian-fish:bullseye
#
# set env
ENV GOLANG_VERSION=1.16.14
ENV PATH /usr/local/go/bin:$PATH

#
# Add HashiCorp Linux repository and install go 1.16.
USER root
SHELL ["/bin/bash", "-c"]
RUN	apt-get update \
    && apt-get install -y --no-install-recommends \
        g++ \
        gcc \
        libc6-dev \
        pkg-config \
    && rm -rf /var/lib/apt/lists/*
RUN curl -o go.tgz https://dl.google.com/go/go$GOLANG_VERSION.linux-amd64.tar.gz \
    && tar -C /usr/local -xzf go.tgz \
    && rm go.tgz \
    && go version
ENV GOPATH=/go
ENV PATH $GOPATH/bin:$PATH
RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH
#
# set env
ENV DEBIAN_FRONTEND=dialog
LABEL org.opencontainers.image.source https://github.com/kumanoryo/dot-devcontainer-golang-1.16