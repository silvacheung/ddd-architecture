FROM docker.io/library/golang:1.23.3-alpine AS builder

ARG PKG=example

WORKDIR /app/src
COPY . .

WORKDIR /app/src/cmd/$PKG
RUN go env -w GOARCH=amd64 && \
    go env -w GO111MODULE=on && \
    go env -w GOPROXY=https://goproxy.cn,direct && \
    go mod tidy && \
    go build -ldflags "-s -w" -o /app/main.app

FROM docker.io/library/alpine:latest

COPY --from=builder /app/main.app /app/main.app

VOLUME /app/config.yaml

EXPOSE 8080

CMD ["/app/main.app", "--config=/app/config.yaml"]