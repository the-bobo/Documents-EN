### backup

```
usage: alauda backup [-h] {create,list,inspect,rm} ...

Backup operations

optional arguments:
  -h, --help            show this help message and exit

Alauda backup commands:
  {create,list,inspect,rm}
    create              Create a new volume backup
    list                List volume backups
    inspect             Get details of a volume backup
    rm                  Remove a volume backup
```


Manage backups for the data volumes used by the services

Example:

```
bash-3.2# alauda backup create backup1 redis /data
[alauda] Creating backup "backup1"
[alauda] OK
```

### create

Create a volume backup


```
usage: alauda backup create [-h] [-n NAMESPACE] name service dir

Create a new volume backup

positional arguments:
  name                  Backup name
  service               Name of the service to create volume backup for
  dir                   Mounted volume directory to backup

optional arguments:
  -h, --help            show this help message and exit
  -n, --namespace=""    Service namespace
```


### list

List volume backups

```
usage: alauda backup list [-h] [-n NAMESPACE]

list volume backups

optional arguments:
  -h, --help            show this help message and exit
  -n, --namespace=""    Service namespace
```


### inspect

Get details of a volume backup


```
usage: alauda backup inspect [-h] [-n NAMESPACE] id

Get details of a volume backup

positional arguments:
  id                    UUID of the volume backup

optional arguments:
  -h, --help            show this help message and exit
  -n, --namespace=""    Service namespace
```




### rm

Remove a volume backup

```
usage: alauda backup rm [-h] [-n NAMESPACE] id

Remove a volume backup

positional arguments:
  id                    UUID of the volume backup

optional arguments:
  -h, --help            show this help message and exit
  -n, --namespace=""    Service namespace
```





