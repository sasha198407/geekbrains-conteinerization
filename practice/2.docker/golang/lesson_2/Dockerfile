FROM golang:alpine as builder

LABEL stage=gobuilder

RUN apk update --no-cache

RUN mkdir /app
COPY . /app
WORKDIR /app

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o main .

FROM scratch

COPY --from=builder /app/main /

EXPOSE 8080

CMD ["/main"]
