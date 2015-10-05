## Services


```
usage: alauda service [-h]

                      {create,run,inspect,start,stop,rm,ps,scale,enable-autoscaling,disable-autoscaling,logs,instances,instance,instance-logs,instance-metrics}
                      ...

Service operations

optional arguments:
  -h, --help            show this help message and exit

Alauda service commands:
  {create,run,inspect,start,stop,rm,ps,scale,enable-autoscaling,disable-autoscaling,logs,instances,instance,instance-logs,instance-metrics}
    create              Create a new service
    run                 Create and start a new service
    inspect             Get details of a service
    start               Start a service
    stop                Stop a service
    rm                  Remove a service
    ps                  List services
    scale               Scale a service
    enable-autoscaling  Enable auto-scaling
    disable-autoscaling Disable auto-scaling
    logs                Query service log
    instances           List instances
    instance            Get details of a instance
    instance-logs       Query instance log
```


Example:

```
bash-3.2# alauda run hello index.alauda.cn/alauda/hello-world:latest -p 80
[alauda] Creating and starting service "hello"
[alauda] OK

```



### create
Create a new service (without starting it).

```
usage: alauda service create [-h] [-t TARGET_NUM_INSTANCES] [-s {XS,S,M,L,XL}]
                             [-r RUN_COMMAND] [-e ENV] [-l LINK] [-p PUBLISH]
                             [-ex EXPOSE] [-v VOLUME] [-n NAMESPACE] [-a]
                             [-f AUTOSCALING_CONFIG] [-d DOMAIN]
                             name image

Create a new service

positional arguments:
  name                  Service name
  image                 Docker image used by the service

optional arguments:
  -h, --help                            show this help message and exit
  -t, --target-num-instances=1          Target number of instances for the service
  -s, --instance-size={XS,S,M,L,XL}     Service container size
  -r, --run-command=""                  The command used to start the service containers
  -e, --env=[]                          Environment variables, e.g. VAR=value
  -l, --link=[]                         which service to link.
  -p, --publish=[]                      Ports to publish, e.g. 5000/tcp
  -ex, --expose=[]                      Internal ports, e.g. 5000
  -v, --volume=[]                       Volumes, e.g. /var/lib/mysql:10
  -n, --namespace=""                    Service namespace
  -a, --autoscale=false                 Enable auto-scaling
  -f, --autoscaling-config=""           Auto-scaling config file name
  -d, --domain=""                       Custom domain name
```


Parameters:

- If `-a` is used to enable auto-scaling, then either use `-f` to specify the auto-scaling config file, or a default config file `auto-scaling.cfg` must exist in the current directory.




### run

Create and start a new service.


```
usage: alauda service run [-h] [-t TARGET_NUM_INSTANCES] [-s {XS,S,M,L,XL}]
                          [-r RUN_COMMAND] [-e ENV] [-l LINK] [-p PUBLISH]
                          [-ex EXPOSE] [-v VOLUME] [-n NAMESPACE] [-a]
                          [-f AUTOSCALING_CONFIG] [-d DOMAIN]
                          name image

Create and start a new service

positional arguments:
  name                  Service name
  image                 Docker image used by the service

optional arguments:
  -h, --help                            show this help message and exit
  -t, --target-num-instances=1          Target number of instances for the service
  -s, --instance-size={XS,S,M,L,XL}     Service container size
  -r, --run-command=""                  The command used to start the service containers
  -e, --env=[]                          Environment variables, e.g. VAR=value
  -l, --link=[]                         which service to link.
  -p, --publish=[]                      Ports to publish, e.g. 5000/tcp
  -ex, --expose=[]                      Internal ports, e.g. 5000
  -v, --volume=[]                       Volumes, e.g. /var/lib/mysql:10
  -n, --namespace=""                    Service namespace
  -a, --autoscale=false                 Enable auto-scaling
  -f, --autoscaling-config=""           Auto-scaling config file name
  -d, --domain=""                       Custom domain name
```



### inspect
Inspect the details of a service.


```
usage: alauda service inspect [-h] [-n NAMESPACE] name

Get details of a service

positional arguments:
  name                  Name of the service to retrieve

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
```






### start

Start a service.


```
usage: alauda service start [-h] [-n NAMESPACE] name

Start a service

positional arguments:
  name                  Name of the service to start

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
  ```



### stop
Stop a service.

```
usage: alauda service stop [-h] [-n NAMESPACE] name

Stop a service

positional arguments:
  name                  Name of the service to stop

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
```


### rm
Deletes a service.


```
usage: alauda service rm [-h] [-n NAMESPACE] name

Remove a service

positional arguments:
  name                  Name of the service to remove

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
```



### ps
List all services for the current user (under an optional namespace).


```
usage: alauda service ps [-h] [-n NAMESPACE]

List services

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
```


### scale

Scale the number of instances of the service.



```

usage: alauda service scale [-h] [-n NAMESPACE] [descriptor [descriptor ...]]

Scale a service

positional arguments:
  descriptor            E.g. web=2

optional arguments:
  -h, --help                show this help message and exit
  -n, --namespace=""        Service namespace
```


### enable-autoscaling

Enable auto-scaling for the service.

```
usage: alauda service enable-autoscaling [-h] [-n NAMESPACE]
                                         [-f AUTOSCALING_CONFIG]
                                         name

Enable auto-scaling

positional arguments:
  name                  Service name

optional arguments:
  -h, --help                        show this help message and exit
  -n, --namespace=""                Service namespace
  -f, --autoscaling-config=""       Auto-scaling config file name
```

Use `-f` to specify the auto-scaling config file. The config file defaults to `auto-scaling.cfg` in the current directory.

### disable-autoscaling

Disable auto-scaling


```
usage: alauda service disable-autoscaling [-h] [-n NAMESPACE]
                                          [-t TARGET_NUM_INSTANCES]
                                          name

Disable auto-scaling

positional arguments:
  name                  Service name

optional arguments:
  -h, --help                    show this help message and exit
  -n, --namespace=""            Service namespace
  -t, --target-num-instances=1  Target number of instances for the service
```

Use `-t` to specify the number of instances. If it is not specified, the current number of instances will be used.


### logs

Query service logs.


```
usage: alauda service logs [-h] [-n NAMESPACE] [-s START_TIME] [-e END_TIME]
                           name

Query service log

positional arguments:
  name                  Service name

optional arguments:
  -h, --help                    show this help message and exit
  -n, --namespace=""            Service namespace
  -s, --start-time=""           Logs query start time. e.g. 2015-05-01 12:12:12
  -e, --end-time=""             Logs query end time. e.g. 2015-05-01 12:12:12
```

If neither `start-time` nor `end-time` is specified, the command returns the most recent one hour worth of log data. If only `start-time` is specified, the command returns all log entries since the `start-time`. If only `end-time` is specified, the command returns one hour worth of log data before the `end-time`.



