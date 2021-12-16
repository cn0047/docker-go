FROM golang:1.16.10-alpine3.15

MAINTAINER V. Kovpak <cn007b@gmail.com>

# OS tools
RUN apk add git make

# Go tools
RUN go get -u golang.org/x/lint/golint && ln -s $GOPATH/bin/golint /usr/bin/
RUN wget -O- -nv https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s v1.43.0
RUN go get -u golang.org/x/tools/cmd/cover
RUN go get -u github.com/mattn/goveralls && ln -s $GOPATH/bin/goveralls /usr/bin/
RUN wget -O - -q https://raw.githubusercontent.com/securego/gosec/master/install.sh | sh -s v2.9.5
