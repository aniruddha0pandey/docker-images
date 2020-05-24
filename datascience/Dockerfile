FROM debian:latest

LABEL version "0.0.1" \
      maintainer "Aniruddha Pandey <anirudh.pandev@gmail.com>"

WORKDIR /app

ENV EMAIL anirudh.pandev@gmail.com
ENV GITHUB_USERNAME pandevim

# Silent Error
ENV DEBIAN_FRONTEND noninteractive
#

# Use Bash as default
SHELL ["/bin/bash", "-c"]
#

# Root privelage
USER root
#

# Install Basic
RUN apt-get update && apt-get -y upgrade && apt-get -y install \
        apt-utils \
        build-essential \
        ca-certificates
#

# Install Helpers
RUN apt-get -y install \
        curl \
        ssh \
        hub \
        jq \
        gnupg2
#

# Python pre-requisites
RUN apt-get -y install \
        python3 \
        python3-pip \
        python3-dev
#

# R pre-requisites
RUN apt-get -y install \
        python3 \
        python3-pip \
        python3-dev
#

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Setup Python Environment
RUN pip3 install -r \
    pandas \
    numpy \
    jupyter
RUN pip3 freeze > requirements.txt
#

# Add Tini. Tini operates as a process subreaper for jupyter. This prevents kernel crashes.
ENV TINI_VERSION v0.6.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini
ENTRYPOINT ["/usr/bin/tini", "--"]
#

# Create SSH keys
RUN ssh-keygen -q \
    -t rsa \
    -C "$EMAIL" \
    -N "" \
    -f ~/.ssh/id_rsa <<< y
#

# https://github.com/jupyter/docker-stacks
# https://www.digitalocean.com/community/tutorials/how-to-install-r-on-debian-10
# https://github.com/austinbrian/jupydocker
# https://www.analyticsvidhya.com/blog/2017/11/reproducible-data-science-docker-for-data-science/
# https://blog.datasciencedojo.com/data-science-with-docker-containers/
# https://www.kdnuggets.com/2018/01/docker-data-science.html
# https://analyticsindiamag.com/docker-playground-for-datascience/
# https://www.dataquest.io/blog/docker-data-science/
# https://www.dataquest.io/blog/docker-data-science/
# https://towardsdatascience.com/how-docker-can-help-you-become-a-more-effective-data-scientist-7fc048ef91d5
# https://towardsdatascience.com/docker-made-easy-for-data-scientists-b32efbc23165
# https://hub.docker.com/r/jupyter/datascience-notebook/
# https://medium.com/applied-data-science/the-full-stack-data-scientist-part-2-a-practical-introduction-to-docker-1ea932c89b57
# 




