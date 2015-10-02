# Login


Use `login` to connect the CLI to one specific Alauda service and login.
Use `-c` to select the cloud to log onto.
`cn` indicates alauda.cn (China, default), and `io` indicates alauda.io (US)
In addition, you could also use `-e` to explicitly specify the Alauda API endpoint. E.g.: `https://api.alauda.io/v1/`

```
usage: alauda login [-h] [-u USERNAME] [-p PASSWORD] [-c {cn,io}]
                    [-e ENDPOINT]

Alauda login

optional arguments:
  -h, --help                    show this help message and exit
  -u, --username=""             Alauda username
  -p, --password=""             Alauda password
  -c {cn,io}, --cloud={cn,io}   Alauda Cloud to connect to
  -e, --endpoint=""             Alauda API endpoint to use
```


Example:

```
bash-3.2# alauda login -c cn -u test -p test
[alauda] Successfully logged in as test.
[alauda] OK

bash-3.2# alauda login -e https://api.alauda.io/v1/ -u test -p test
[alauda] Successfully logged in as test.
[alauda] OK
```


## Logout

Logout from the Alauda service.

```
usage: alauda logout [-h]

Log out

optional arguments:
  -h, --help  show this help message and exit
```


Example:
```
bash-3.2# alauda logout
[alauda] Bye
[alauda] OK
```

  
