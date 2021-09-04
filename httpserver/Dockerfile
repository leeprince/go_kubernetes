FROM golang:alpine

RUN mkdir /build

WORKDIR /build

COPY . /build

ARG CGO=0
ENV CGO_ENABLED=${CGO}
ENV GOARCH=amd64
ENV GOOS=linux
ENV GO111MODULE=on

RUN set -ex && \
	go mod tidy && \
	CGO_ENABLED=${CGO_ENABLED} GOARCH=${GOARCH} GOOS=${GOOS} go build -a -o go_k8s_httpserver ./main.go

# [推荐]
ENTRYPOINT ["./go_k8s_httpserver"]
#CMD ["./go_k8s_httpserver"]