FROM golang:1.8
WORKDIR /build
COPY app.go /build/app.go
RUN go get github.com/gorilla/mux
ENV CGO_ENABLED=0
ENV GOOS=linux
RUN go build -ldflags "-s" -a -installsuffix cgo -o hello-world

FROM scratch
WORKDIR /app
COPY --from=0 /build/hello-world /app/hello-world
CMD [ "/app/hello-world" ]
