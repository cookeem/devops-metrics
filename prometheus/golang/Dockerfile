FROM alpine:edge
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk add --no-cache ca-certificates
COPY main /main
EXPOSE 8080
CMD ["/main"]
