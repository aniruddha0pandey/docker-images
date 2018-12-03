FROM openjdk:8-slim

LABEL maintainer "Aniruddha Pandey (pandevim) <anirudh.pandev@gmail.com>"

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    git \
    lib32stdc++6 \
    libglu1-mesa \
    gnupg \
    apt-transport-https \
    sudo && \
    rm -rf /var/lib/apt/lists/*

# RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8

ENV SDK_TOOLS "3859397"
ENV BUILD_TOOLS "27.0.3"
ENV TARGET_SDK "27"
ENV ANDROID_HOME "/opt/sdk"

# Download and extract Android Tools
RUN curl -L http://dl.google.com/android/repository/sdk-tools-linux-${SDK_TOOLS}.zip -o /tmp/tools.zip --progress-bar && \
    mkdir -p ${ANDROID_HOME} && \
    unzip /tmp/tools.zip -d ${ANDROID_HOME} && \
    rm -v /tmp/tools.zip

# Install SDK Packages
RUN mkdir -p /root/.android/ && touch /root/.android/repositories.cfg && \
    yes | ${ANDROID_HOME}/tools/bin/sdkmanager "--licenses" && \
    ${ANDROID_HOME}/tools/bin/sdkmanager "--update" && \
    ${ANDROID_HOME}/tools/bin/sdkmanager "build-tools;${BUILD_TOOLS}" "platform-tools" "platforms;android-${TARGET_SDK}" "extras;android;m2repository" "extras;google;google_play_services" "extras;google;m2repository"

# Install flutter
ENV FLUTTER_HOME "/opt/flutter"
ENV FLUTTER_VERSION "v0.11.13-beta"
RUN mkdir -p ${FLUTTER_HOME} && \
    curl -L http://storage.googleapis.com/flutter_infra/releases/beta/linux/flutter_linux_${FLUTTER_VERSION}.tar.xz -o /tmp/flutter.tar.xz --progress-bar && \
    tar xf /tmp/flutter.tar.xz -C /tmp && \
    mv /tmp/flutter/ -T ${FLUTTER_HOME} && \
    rm -rf /tmp/flutter.tar.xz

ENV PATH=$PATH:$FLUTTER_HOME/bin

# Install Visual Studio Code
RUN curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && \
    install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/ && \
    sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'

# vscode dependencies
RUN apt-get -y --no-install-recommends install \
    libc6-dev \
    libgtk2.0-0 \
    libgtk-3-0 \
    libpango-1.0-0 \
    libcairo2 \
    libfontconfig1 \
    libgconf2-4 \
    libnss3 \
    libasound2 \
    libxtst6 \
    unzip \
    libglib2.0-bin \
    libcanberra-gtk-module \
    libgl1-mesa-glx \
    build-essential \
    gettext \
    libstdc++6 \
    software-properties-common \
    wget \
    xterm \
    automake \
    libtool \
    autogen \
    nodejs \
    libnotify-bin \
    aspell \
    aspell-en \
    htop \
    mono-complete \
    gvfs-bin \
    libxss1 \
    rxvt-unicode-256color \
    x11-xserver-utils \
    vim \
    libxkbfile1

RUN apt-get update && \
    apt-get install -y code
    

