FROM golang:1.16-alpine3.13

RUN apk --no-cache add curl
ARG ARCH=linux_arm64
ENV GO_SWAGGER_VERSION=0.28.0 \
    REPO="github.com/go-swagger/go-swagger"

RUN curl -SL "https://${REPO}/archive/refs/tags/v${GO_SWAGGER_VERSION}.tar.gz" -o /tmp/go-swagger.tar.gz 

WORKDIR /swaggers

RUN mkdir /tmp/go-swagger \ 
    && tar zxvf /tmp/go-swagger.tar.gz -C /tmp \
    && cd /tmp/go-swagger-"${GO_SWAGGER_VERSION}" \
    && go build -o swagger ./cmd/swagger/swagger.go \
    && mv swagger /usr/bin/swagger

RUN apk del curl \
    && rm -rf /tmp/*

CMD ["sh"]