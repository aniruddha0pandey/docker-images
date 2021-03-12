FROM pandevim/web:latest

LABEL version "0.0.1" \
      maintainer "Aniruddha Pandey <anirudh.pandev@gmail.com>"

WORKDIR /app

SHELL ["/bin/bash", "-c"]

USER root

# https://developer.android.com/studio/index.html#command-tools
ARG SDK_PACKAGE_NAME commandlinetools-linux-6858069_latest.zip

# Got from https://source.android.com/setup/start/build-numbers
ARG ANDROID_API_VERSION 30

# Got from https://developer.android.com/studio/releases/build-tools
ARG ANDROID_TOOLS_VERSION 29.0.2

# Got from https://developer.android.com/ndk/downloads
ARG NDK_VERSION 22.0.7026061

ENV ANDROID_HOME=/opt/android
ENV PATH=${ANDROID_HOME}/ndk/${NDK_VERSION}:${ANDROID_HOME}/cmdline-tools/cmdline-tools/bin:${ANDROID_HOME}/platform-tools:${ANDROID_HOME}/tools:${ANDROID_HOME}/tools/bin:/opt/buck/bin/:${PATH}

# Install JDK
RUN apt update -qq && apt install -qq -y --no-install-recommends \
		openjdk-11-jdk-headless \
		unzip

# Install skdmanager
RUN curl -sS https://dl.google.com/android/repository/${SDK_PACKAGE_NAME} -o /tmp/sdk.zip && \
		mkdir -p ${ANDROID_HOME}/cmdline-tools && \
		unzip -q -d ${ANDROID_HOME}/cmdline-tools /tmp/sdk.zip && \
		rm /tmp/sdk.zip

# Install Android SDK packages
RUN yes | sdkmanager --licenses && \
		yes | sdkmanager \
			"platform-tools" \
			"platforms;android-$ANDROID_API_VERSION" \
			"build-tools;$ANDROID_TOOLS_VERSION" \
			"ndk;$NDK_VERSION" && \
		rm -rf ${ANDROID_HOME}/.android

# Install latest node version
RUN nvm install node

# Install react-native-cli globally
RUN npm install -g react-native-cli

CMD ["/bin/bash"]

