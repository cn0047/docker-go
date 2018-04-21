FROM cn007b/ubuntu:17.10

MAINTAINER Vladimir Kovpak <cn007b@gmail.com>

ENV GOROOT /usr/local/go/
ENV GOPATH /app/
RUN mkdir /app

RUN curl -O https://storage.googleapis.com/golang/go1.10.linux-amd64.tar.gz \
    && tar zxf go1.10.linux-amd64.tar.gz \
    && rm go1.10.linux-amd64.tar.gz \
    && mv go /usr/local \
    && ln -s /usr/local/go/bin/go /usr/bin/

RUN go get -u golang.org/x/lint/golint
RUN go get -u golang.org/x/tools/cmd/cover
RUN go get -u github.com/mattn/goveralls

CMD ["/usr/bin/go"]
