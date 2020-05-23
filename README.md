# docker-images
Emphasis [Gang-of-Four](http://www.uml.org.cn/c++/pdf/DesignPatterns.pdf#) Builder Design Pattern.

## Build
```bash
$ # Build Image from Dockefile
$ docker build --tag <image-name> .
```
```bash
$ # Push to DockerHub
$ docker tag web pandevim/<image-name>:latest
$ docker push pandevim/<image-name>:latest
```
## Usage
```bash
$ docker pull pandevim/<image-name>
```
```bash
$ git clone https://github.com/pandevim/docker-images.git
$ cd docker-images/<image-name>
$ docker build --tag <image-name> .
```
