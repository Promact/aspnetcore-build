FROM microsoft/aspnetcore-build:2

RUN curl -o- -L https://yarnpkg.com/install.sh | bash

RUN curl -o /usr/local/bin/ecs-cli https://s3.amazonaws.com/amazon-ecs-cli/ecs-cli-linux-amd64-latest && chmod +x /usr/local/bin/ecs-cli

# Let's start with some basic stuff.
RUN apt-get update -qq && apt-get install -qqy \
    apt-transport-https \
    ca-certificates \
    curl \
    lxc \
    iptables \
    bzip2 \
    python-pip \
    unzip \
    libfontconfig \
    jq --no-install-recommends

RUN curl -sSL https://get.docker.com/ | sh
