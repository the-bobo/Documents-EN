## Alauda Command Line

## Source code
Alauda CLI is open sourced at:

`https://github.com/alaudacloud/alauda-CLI.git`


## Installation

`pip install alauda`


## Usage
`alauda` or `alauda -h`:

```
bash-3.2# alauda
usage: alauda [-h] [-v] {login,logout,service,compose,backup,organization} ...

Alauda CLI

optional arguments:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit

Alauda CLI commands:
  {login,logout,service,compose,backup,organization}
    login               Alauda login
    logout              Log out
    service             Service operations
    compose             Compose multi-container app
    backup              Backup operations
    organization        Organization operations
```


Use `-v` to check the version of the installed Alauda CLI:

```
bash-3.2# alauda -v
alauda 0.1.0
```

Understanding the parameters:

* `-e[]` indicates that the option can be repeated multiple times
  E.g. `-e DB_NAME=mysql -e DB_PASSOWRD=123`
* `-d=""` indicates that the value is a string
  E.g. `-d "www.myself-domain.com"`
* `-s=[XS,S,M,L,XL]` indicates that the value must be selected from the set
  E.g. : `-s XL`
* `-t=1` indicates that the value is numeric
  E.g. : `-t 1`
* `-a=false` indicates a binary switch that defaults to `false`



## Help
To get help for any command or subcommand, append the `-h` option:


```
bash-3.2# alauda service create -h
usage: alauda service create [-h] [-t TARGET_NUM_INSTANCES] [-s {XS,S,M,L,XL}]
                             [-r RUN_COMMAND] [-e ENV] [-l LINK] [-p PUBLISH]
                             [-v VOLUME] [-n NAMESPACE] [-a]
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



