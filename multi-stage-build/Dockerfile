FROM golang:alpine

WORKDIR /app

COPY ./hello.go ./hello.go

RUN go build -o hello

CMD ["./hello"]
