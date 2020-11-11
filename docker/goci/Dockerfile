FROM golang:buster

# Perpare
RUN apt-get update && apt-get install -y --no-install-recommends \
        bash \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg2 \
        software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"

# Install desired tools
RUN apt-get update && apt-get install -y --no-install-recommends \
        git \
	gawk \
        docker-ce \
        docker-ce-cli \
        containerd.io
RUN go get -u golang.org/x/lint/golint
RUN go get -u github.com/khezen/cmtpr/cmd/cmtpr
RUN curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b $(go env GOPATH)/bin v1.32.2
