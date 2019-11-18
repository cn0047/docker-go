FROM cn007b/ubuntu:18.04

MAINTAINER Vladimir Kovpak <cn007b@gmail.com>

ARG GOLANG_ARCHIVE=go1.13.linux-amd64.tar.gz

ENV GOROOT /usr/local/go/
ENV GOPATH /opt/cn007b/go/
RUN mkdir -p $GOPATH

# go
RUN curl -O https://storage.googleapis.com/golang/$GOLANG_ARCHIVE \
    && tar zxf $GOLANG_ARCHIVE \
    && rm $GOLANG_ARCHIVE \
    && mv go /usr/local \
    && ln -s /usr/local/go/bin/go /usr/bin/

# tools
RUN apt-get install go-dep
RUN go get -u golang.org/x/lint/golint && ln -s $GOPATH/bin/golint /usr/bin/
RUN go get -u github.com/golangci/golangci-lint/cmd/golangci-lint \
  && ln -s $GOPATH/bin/golangci-lint /usr/bin/
RUN go get -u golang.org/x/tools/cmd/cover
RUN go get -u github.com/mattn/goveralls && ln -s $GOPATH/bin/goveralls /usr/bin/
RUN go get -u github.com/derekparker/delve/cmd/dlv && ln -s $GOPATH/bin/dlv /usr/bin/
RUN go get -u github.com/codegangsta/gin && ln -s $GOPATH/bin/gin /usr/bin/
RUN curl -sfL https://raw.githubusercontent.com/securego/gosec/master/install.sh \
  | sh -s -- -b $GOPATH/bin v2.1.0 && ln -s $GOPATH/bin/gosec /usr/bin/
RUN go get -u github.com/google/pprof && ln -s $GOPATH/bin/pprof /usr/bin/
# required for pprof
RUN apt install -y python-pydot python-pydot-ng graphviz

CMD ["/usr/bin/go"]
