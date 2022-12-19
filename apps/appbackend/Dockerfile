FROM --platform=linux golang:alpine as build
WORKDIR /src

COPY go.mod go.sum ./
RUN go mod download

COPY *.go ./
RUN go build -o /build

FROM --platform=linux alpine:latest
WORKDIR /

COPY --from=build /build /app
EXPOSE 9080
ENTRYPOINT [ "/app" ]

