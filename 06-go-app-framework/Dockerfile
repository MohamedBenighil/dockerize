# syntax = docker/dockerfile:1.3
FROM golang:1.15-alpine3.14 as build
WORKDIR /code
COPY ./gin-helloworld/go.mod ./gin-helloworld/go.sum .
RUN  --mount=type=cache,target=/root/.cache/ go mod download
COPY ./gin-helloworld/main.go .
RUN --mount=type=cache,target=/root/.cache/  go build -o app

FROM alpine:3.14 as runner 
WORKDIR /code
COPY --from=build /code/app .
CMD [ "./app" ]

#http://localhost:8080/ping