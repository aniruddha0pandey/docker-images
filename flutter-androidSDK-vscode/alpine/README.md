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
$ NAME=""
$ ENVR="Alias" # This may be conflicting
$ VERSION="a-b-c-d"
$ docker build -f build.dockerfile -t NAME-ENV-VERSION .
```
