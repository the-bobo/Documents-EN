## organization

```
usage: alauda organization [-h] {list,create,inspect,update} ...

Organization operations

optional arguments:
  -h, --help            show this help message and exit

Alauda organization commands:
  {list,create,inspect,update}
    list                List all organization
    create              Create a new organization
    inspect             Get details of an organization
    update              Update an exist orgnization

```


Create an organization under the current account. Admins of the organization can add and remove users and manage their permissions. Permissions could be read-only, read-write, or admin.

Example:

```
bash-3.2# alauda organization list
     Name           Company              Created time
-----------------------------------------------------------
dev              Mathilde Tech     2015-04-25T05:42:00.828Z
frontend-dev     Mathilde Tech     2015-05-19T03:35:29.047Z
backend-dev      Mathilde Tech     2015-05-25T07:38:07.670Z

```



### create
Create a new organization

```
usage: alauda organization create [-h] name company

Create a new organization

positional arguments:
  name        Organization name
  company     Company name

optional arguments:
  -h, --help  show this help message and exit
  ```


### list

List all organizations this user belong to.


### inspect

Get details of an organization


```
usage: alauda organization inspect [-h] name

Get details of an organization

positional arguments:
  name        Organization name

optional arguments:
  -h, --help  show this help message and exit
```

### update

Update an organization



```
usage: alauda organization update [-h] name company

Update an exist orgnization

positional arguments:
  name        Organization name
  company     Company name

optional arguments:
  -h, --help  show this help message and exit
```


