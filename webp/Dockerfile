FROM ubuntu:latest
LABEL MAINTAINER Isidro Salcedo <salcedo.isidro@gmail.com>

ENV WEBP_HOME /usr/local/webp
ENV PATH $WEBP_HOME/bin:$PATH
RUN mkdir -p "$WEBP_HOME"

WORKDIR $WEBP_HOME

ENV WEBP_FILE libwebp-1.0.1.tar.gz
ENV LD_LIBRARY_PATH /usr/local/lib/

RUN apt-get update && \
    apt-get install -y libjpeg-dev libpng-dev libtiff-dev libgif-dev wget; \
    wget -O libwebp.tar.gz https://storage.googleapis.com/downloads.webmproject.org/releases/webp/${WEBP_FILE}; \
    buildDir="$(mktemp -d)"; \
    tar -xvf libwebp.tar.gz -C "$buildDir" --strip-components=1; \
    ( \
    cd "$buildDir"; \
    ./configure; \
    make -j $(nproc); \
    make install; \
    ); \
    rm -rf "$buildDir"; \
    rm -rf libwebp.tar.gz;