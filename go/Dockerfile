FROM golang:stretch as builder
LABEL maintainer "Newerton Vargas de Araujo <newerton.araujo@gmail.com>"

WORKDIR $GOPATH/src/webserver/
COPY . /go/
RUN CGO_ENABLED=0 GOOS=linux go build -a -ldflags "-s -w" main.go
RUN chmod +x main.go

FROM scratch
LABEL maintainer "Newerton Vargas de Araujo <newerton.araujo@gmail.com>"

COPY --from=builder /go/src/webserver/main .

EXPOSE 8000
ENTRYPOINT ["./main"]