FROM alpine:latest as builder

ARG version="1.1.3"

ENV DOWNLOAD_URL=https://github.com/mayswind/AriaNg/releases/download/${version}/AriaNg-${version}.zip
ENV FILE_NAME=AriaNg-${version}.zip

WORKDIR /opt/ariang

RUN set -ex && \
    wget --no-check-certificate -q ${DOWNLOAD_URL} -O ${FILE_NAME} && \
    unzip ${FILE_NAME} && \
    rm ${FILE_NAME}

FROM nginx:stable-alpine

COPY --from=builder /opt/ariang /usr/share/nginx/html