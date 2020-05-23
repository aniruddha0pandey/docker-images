# docker-images
Emphasis [Gang-of-Four](http://www.uml.org.cn/c++/pdf/DesignPatterns.pdf#) Builder Design Pattern.

```bash
$ # Build Image from Dockefile
$ docker build --tag <image-name> .
```
```bash
$ # Push to DockerHub
$ docker tag web pandevim/<image-name>:latest
$ docker push pandevim/<image-name>:latest
```
