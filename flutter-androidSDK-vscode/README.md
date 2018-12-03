Thanks [Álvaro S.](https://github.com/alvr/alpine-android) for binding android-sdk with [`openjdk:8-slim`](https://github.com/docker-library/openjdk/tree/master/8).

```
$ docker pull pandevim/flutter-androidSDK-vscode
$ # OR
$ git clone https://github.com/aniruddha0pandey/docker-images.git && cd docker-images/flutter-androidSDK-vscode/<distro>
$ docker build -t [image-name] .
$ docker run -it --entrypoint=/bin/bash [image-name]
```
