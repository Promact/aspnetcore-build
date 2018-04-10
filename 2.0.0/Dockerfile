FROM microsoft/dotnet:2.0.6-sdk-2.1.101-stretch

# set up environment
ENV ASPNETCORE_URLS http://+:80
ENV ASPNETCORE_PKG_VERSION 2.0.6

# set up node
ENV NODE_VERSION 8.11.1
ENV NODE_DOWNLOAD_SHA 0e20787e2eda4cc31336d8327556ebc7417e8ee0a6ba0de96a09b0ec2b841f60
ENV NODE_DOWNLOAD_URL https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.gz

RUN curl -SL "$NODE_DOWNLOAD_URL" --output nodejs.tar.gz \
    && echo "$NODE_DOWNLOAD_SHA nodejs.tar.gz" | sha256sum -c - \
    && tar -xzf "nodejs.tar.gz" -C /usr/local --strip-components=1 \
    && rm nodejs.tar.gz \
    && ln -s /usr/local/bin/node /usr/local/bin/nodejs    

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
    python-setuptools \
    libfontconfig \
    jq --no-install-recommends

RUN curl -sSL https://get.docker.com/ | sh

RUN pip install awscli --upgrade

RUN curl -sSL https://github.com/SonarSource/sonar-scanner-msbuild/releases/download/4.1.1.1164/sonar-scanner-msbuild-4.1.1.1164-netcoreapp2.0.zip --output sonar.zip \
  && unzip sonar.zip -d /opt/sonar \
  && rm -rf sonar.zip