FROM golang:stretch as builder
LABEL maintainer "Newerton Vargas de Araujo <newerton.araujo@gmail.com>"

WORKDIR $GOPATH/src/webserver/
COPY /src .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -v

FROM scratch
LABEL maintainer "Newerton Vargas de Araujo <newerton.araujo@gmail.com>"

COPY --from=builder go/src/webserver/webserver .

EXPOSE 8000
ENTRYPOINT ["./webserver"]