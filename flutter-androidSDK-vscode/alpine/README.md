Update: 16-12-18  

| Base | Version |
|-|-|
| Alpine | a |
| JDK | b |
| Android | c |
| Flutter | d |

```
$ VERSION="a-b-c-d"
$ docker build -f build.dockerfile -t flutter-build-VERSION .
$ # OR
$ docker build -f prod.dockerfile -t flutter-prod-VERSION .
```
