FROM alpine:3.7

RUN \
  apk add --update go git make gcc musl-dev linux-headers ca-certificates && \
  git clone --depth 1 --branch release/1.8 https://github.com/ethersocial/go-ethersocial && \
  (cd go-ethersocial && make geth) && \
  cp go-ethersocial/build/bin/geth /geth && \
  apk del go git make gcc musl-dev linux-headers && \
  rm -rf /go-ethersocial && rm -rf /var/cache/apk/*

EXPOSE 9545
EXPOSE 50505

ENTRYPOINT ["/geth"]
