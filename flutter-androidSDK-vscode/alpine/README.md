Update: 16-12-18  

| Base | Version |
|-|-|
| Alpine | a |
| JDK | b |
| Android | c |
| Flutter | d |

| Environment | Alias |
|-|-|
| Building | build |
| Production | prod |
| Development | dev |
| Testing | test |

```
$ # ENV="Alias"
$ VERSION="a-b-c-d"
$ docker build -f build.dockerfile -t flutter-ENV-VERSION .
```
