FROM golang:alpine3.15 AS build
WORKDIR /code
COPY  ./src/ .
RUN go build app.go
RUN go build app.go

FROM alpine:3.15.0 as runner
WORKDIR /artifact
COPY --from=build ./code/app ./
CMD ["./app"]