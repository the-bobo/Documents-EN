## Retrieve user information

`GET /v1/auth/(namespace)/profile/`

**Sample response** :
```json
{
  "id": 5,
  "last_login": "2015-02-17T07:35:06.253Z",
  "username": "ruicao",
  "email": "ruicao@mathildetech.com",
  "realname": "RuiCao",
  "prefered_language": "zh-cn",
  "is_active": true,
  "is_trialuser": true,
  "password_is_temp": false,
  "joined_at": "2015-02-17T07:35:06.300Z",
  "currency": "CNY",
  "account_type": 1,
  "is_available": true,
  "user_level": "unlimited",
  "company": null,
  "company_website": "",
  "company_size": 0,
  "industry": 0,
  "mobile": null,
  "feature_flags": 65535,
  "logo_file": "https://alauda-cn-jakiro.s3.cn-north-1.amazonaws.com.cn/user/ruicao/logo1434463257.jpg",
  "app_created": "2015-08-04T03:10:49.999Z",
  "repo_created": "2015-07-27T10:34:56.922Z",
  "api_revoked": "2015-08-05T09:09:03.432Z",
  "type": "test"
}
```


## Generate API token

`POST /v1/generate-api-token/`


**Sample request** :
```json
{
    "username": "madams",
    "password": "a1b2c3d4"
}
```

**Sample response** :
```json
{
    "token": "4dfff64b6d2994a9567ac363149fb8692273e6b2"
}​
```

