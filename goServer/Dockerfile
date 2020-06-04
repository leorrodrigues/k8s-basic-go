FROM golang:1.13 AS builder

WORKDIR /go/src/server
COPY src/*.go /go/src/server/

RUN GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o /go/bin/server

FROM scratch

COPY --from=builder /go/bin/server /server

ENTRYPOINT [ "/server" ]