FROM microsoft/aspnetcore-build:2.0.0-stretch

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

RUN pip install docker-compose

RUN cd /root && curl -OL https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.0.3.778-linux.zip && \
     unzip sonar-scanner-cli-3.0.3.778-linux.zip && \
     ln -fs /root/sonar-scanner-3.0.3.778-linux/bin/sonar-scanner /usr/bin/sonar-scanner && \
     rm -rf sonar-scanner-cli-3.0.3.778-linux.zip

RUN npm i -g tslint typescript
