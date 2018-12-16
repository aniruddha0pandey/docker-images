> `Update: 16-12-18`

<table>
<tr><th>Packages</th>
<th>Instances</th></tr>
<tr>
<td>
  
| Base | Version |
|-|-|
| Alpine | a |
| JDK | b |
| Android | c |
| Flutter | d |

</td>
<td>
  
| Environment | Alias |
|-|-|
| Building | build |
| Production | prod |
| Development | dev |
| Testing | test |

</td>
</tr>
</table>

```bash
$ NAME=""
$ ENVR="Alias" # This may be conflicting
$ VERSION="a-b-c-d"
$ docker build -f build.dockerfile -t NAME-ENV-VERSION .
```
