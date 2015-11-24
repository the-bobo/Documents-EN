## Instances


### instance

Inspect details of a service instance


```
usage: alauda service instance [-h] [-n NAMESPACE] name id

Get details of an instance

positional arguments:
  name                  Service name
  id                    Instance uuid

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
```





### instance-logs

Query logs of a service instance



```
usage: alauda service instance-logs [-h] [-s START_TIME] [-e END_TIME]
                                    [-n NAMESPACE]
                                    name id

Query instance log

positional arguments:
  name                  Service name
  id                    Instance uuid

optional arguments:
  -h, --help                    show this help message and exit
  -s, --start-time=""           Logs query start time. e.g. 2015-05-01 12:12:12
  -e, --end-time=""             Logs query end time. e.g. 2015-05-01 12:12:12
  -n, --namespace=""            Service namespace
```
