# Recipe

## Dockerfile for building "hello world" Go app 

```
FROM golang:1.17.4

WORKDIR /app


COPY go.mod /app/
COPY go.sum /app/

RUN go mod download

COPY . .

CMD ["go", "run", "main.go"]
```