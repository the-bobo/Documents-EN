## Compose

```
usage: alauda compose [-h] {up,ps,start,stop,restart,rm,scale} ...

Compose multi-container app

optional arguments:
  -h, --help            show this help message and exit

Alauda compose commands:
  {up,ps,start,stop,restart,rm,scale}
    up                  Create and start all service containers
    ps                  List containers
    start               Start all service containers
    stop                Stop all service containers
    restart             Restart all service containers
    rm                  Remove all service containers
    scale               Set number of containers to run for a service
```


Alauda compose is used to define and manage a multi-container, multi-service application. It uses the familiar syntax of docker-compose with Alauda-specific capabilities added.

Example:

```
bash-3.2# alauda compose up -f gitlab.alauda.yml
[alauda] Creating and starting service "postgresql"
[alauda] Creating and starting service "redis"
[alauda] Creating and starting service "gitlab"
[alauda] OK
```



Note:

* Syntax for `volumes` is `path:size`, where `size` is the size of the persistent data volume, in gygabytes. The default volume size is 10G. E.g.:

```yaml
volumes:
- /data:10
- /mnt
```


* Only the container ports can be specified in `ports`. E.g.:

```yaml
ports:
- "80"
- "22"
or
ports:
- "80/http"
- "22/tcp"
```

Ports published with `ports` are `external`, that is, they are accessible from outside of the application.


* `expose` has the same syntax as `ports`. These ports are `internal`, meaning they are only accessible to linked services.


* Note that all ports need to be exposed or published with `expose` or `ports`, even if they are already specified in the Dockerfile.


* The value of an environment variable specified in `environment` supports one level of environment substitution. E.g.:

```yaml
DB_HOST: $POSTGRESQL_PORT_5432_TCP_ADDR
The value of DB_HOST is set as the value of $POSTGRESQL_PORT_5432_TCP_ADDR in the current environment.

```

* Use `size` to specify the size of the container. Valid options are {'XS', 'S', 'M', 'L', 'XL'}. E.g.:

```yaml
size: L
```

* Use `domain` to specify a custom domain. E.g.:

```yaml
domain: "www.myself.com"
```

* Use `autoscaling_config` to specify the configuration file for auto-scaling. E.g.:

```yaml
autoscaling_config: ./autoscaling.cfg
```

* Use `number` to specify the number of instances for a service container. E.g.:

```yaml
size: 5
```


### up

Deploy a multi-service, multi-container application.

```
usage: alauda compose up [-h] [-f FILE] [-s]

Create and start all service containers

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
  -s, --strict=false    Wait for linked services to start
```

When `-s` is used, dependent services will wait for linked services to enter running state before they start.


### ps
List all services under the current application (as defined by the yaml file).

```
usage: alauda compose ps [-h] [-f FILE]

Lists container

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
```


### start

Start a service.

```
usage: alauda compose start [-h] [-f FILE] [-s]

Start all service containers

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
  -s, --strict          Wait for linked services to start
```




### stop

Stop a service.


```
usage: alauda compose stop [-h] [-f FILE]

Stop all service containers

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
```


### restart

Restart a service.

```
usage: alauda compose restart [-h] [-f FILE] [-s]

Restart all service containers

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
  -s, --strict          Wait for linked services to start
```


### rm
Delete a service.

```
sage: alauda compose rm [-h] [-f FILE]

Remove all service containers

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
```


### scale

Scale the number of instances of a service.


```
usage: alauda compose scale [-h] [-f FILE] [descriptor [descriptor ...]]

Set number of containers to run for a service

positional arguments:
  descriptor            E.g. web=2 db=1

optional arguments:
  -h, --help            show this help message and exit
  -f, --file=""         Compose file name
```


Example:

`alauda compose scale web=2 redis=3`






