FROM golang:1.13.5-alpine3.10 AS builder

WORKDIR /build


ENV GOPROXY https://goproxy.cn

COPY go.mod .
#COPY go.sum .
RUN go mod download

COPY . .
RUN go build  -o httpservice .

FROM alpine:3.10 AS final

LABEL  user=gqa version=v1

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
      echo "Asia/Shanghai" > /etc/timezone && \
      mkdir -p /var/log/iam \

WORKDIR /app

COPY --from=builder /build/httpservice /app/

EXPOSE 80

ENTRYPOINT ["/app/httpservice"]
CMD ["-v 3"]
