FROM golang:1.24-alpine

WORKDIR /app
RUN apk add --no-cache curl

COPY go.mod ./

RUN go mod tidy

COPY main.go ./

RUN go build -o service1 .

EXPOSE 8001

CMD ["./service1"]
