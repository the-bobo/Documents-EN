# 登录


Login命令是用于登录灵雀云中国区或者美国区系统。
`-c`选项可以简单的指明所登录的系统。
`cn`为中国区（默认），`io`为美国区。
当然，您也可以使用`-e`参数来直接指明需要登录的地址，例如:`https://api.alauda.io/v1/`

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


样例：

```
bash-3.2# alauda login -c cn -u test -p test
[alauda] Successfully logged in as test.
[alauda] OK

bash-3.2# alauda login -e https://api.alauda.io/v1/ -u test -p test
[alauda] Successfully logged in as test.
[alauda] OK
```


## 退出

退出登录

```
usage: alauda logout [-h]

Log out

optional arguments:
  -h, --help  show this help message and exit
```


示例：
```
bash-3.2# alauda logout
[alauda] Bye
[alauda] OK
```

  
