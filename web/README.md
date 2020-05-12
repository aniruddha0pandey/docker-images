






```bash
$ # Create Dockefile
$ cat > Dockerfile << EOF
FROM debian:latest

MAINTAINER "Aniruddha Pandey" <anirudh.pandev@gmail.com>
LABEL stack="node" version="0.0.2"

WORKDIR /app

ENV NVM_VERSION=v0.35.3
ENV EMAIL=anirudh.pandev@gmail.com
ENV GITHUB_USERNAME=pandevim

SHELL ["/bin/bash", "-c"]

RUN apt-get update -y
RUN DEBIAN_FRONTEND=noninteractive && apt-get install -y \
        apt-utils \
        build-essential \
        ca-certificates \
        curl \
        ssh \
        hub \
        jq \
        gnupg2 && \
    apt-get clean

RUN ssh-keygen -q \
    -t rsa \
    -C "$EMAIL" \
    -N "" \
    -f ~/.ssh/id_rsa <<< y

RUN url=https://raw.githubusercontent.com/pandevim/dotfiles/master/.scripts/download_scripts.sh && \
    curl --compressed -o ~/download_scripts.sh $url && \
    chmod +x ~/download_scripts.sh

RUN hub config --global user.email "$EMAIL" && \
    hub config --global user.name "$GITHUB_USERNAME"

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/$NVM_VERSION/install.sh | bash
RUN source ~/.profile && \
    nvm install node && \
    curl --compressed -o- -L https://yarnpkg.com/install.sh | bash
EOF
```
```bash
$ # Build Image from Dockefile
$ docker build --tag web .
```
$ # Push to DockerHub
$ docker tag web pandevim/web:latest
$ docker push pandevim/web:latest
```
