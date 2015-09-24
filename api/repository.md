## Create an image repo

`POST /v1/repositories/(namespace)/`

**Sample request**:
```json
{
    "repo_name": "repo",
    "description": "A docker image repository",
    "namespace": "madams",
    "is_public": true
}
```

Parameters:
- **repo_name** Image repo name
- **namespace** Username or organization that the image repo belongs to
- **is_public** True if the image repo is public
- **description** Image repo description




**Sample response**:
```json
{
    "repo_name": "repo",
    "namespace": "madams",
    "repo_path": "madams/repo",
    "is_automated": False,
    "description": "A repo docker image repository",
    "creation_time": "2014-11-19T05:54:22.741Z",
    "updated_time": "2014-11-19T05:54:22.741Z",
    "is_public": true,
    "logo": "default-icon.jpg"
}
```

Parameters:

- **is_automated** True if builds can be automatically triggered from a linked source code repository



## List image repos

`GET /v1/repositories/(namespace)/`

**Sample response**:
```json
{
    "count":  3,
    "next": null,
    "previous": null,
    "results": [
        {
            "repo_name": "repo1",
            "namespace": "madams",
            "repo_path": "madams/repo1",
            "is_automated": False,
            "description": "repo1",
            "creation_at": "2014-11-19T05:54:22.741Z",
            "updated_at": "2014-11-19T05:54:22.741Z",
            "is_public": true,
            "logo": "default-icon.jpg",
            "repo_starred_count": 0,
            "full_description": "",
            "download": 0,
            "upload": 9,
            "pulled_at": null,
            "pushed_at": "2015-06-04T16:30:27.532Z"
        },
        {
            "repo_name": "repo2",
            "namespace": "madams",
            "repo_path": "madams/repo2",
            "is_automated": False,
            "description": "repo2",
            "creation_at": "2014-11-19T05:55:42.741Z",
            "updated_at": "2014-11-19T05:55:42.741Z",
            "is_public": true,
            "logo": "default-icon.jpg"
            "repo_starred_count": 0,
            "full_description": "",
            "download": 0,
            "upload": 9,
            "pulled_at": null,
            "pushed_at": "2015-06-04T16:30:27.532Z"
        }
    ]
}
```

## Update an image repo

`PUT /v1/repositories/(namespace)/(repo-name)`


**Sample response**:
```json
{
    "repo_name": "repo",
    "namespace": "madams",
    "repo_path": "madams/repo",
    "description": "A repo docker image repository",
    "is_public": true,
    "logo": "default-icon.jpg"
}
```

## Retrieve image repo details

`GET /v1/repositories/(namespace)/(repo-name)`

**Sample response**:
```json
{
    "namespace": "madams",
    "repo_name": "test",
    "repo_path": "madams/test",
    "logo_file": "/static/images/user/default-logo.png",
    "description": "test",
    "full_description": "test contain 2 tags",
    "repo_starred_count": 0,
    "created_at": "2015-05-13T01:04:48.246Z",
    "updated_at": "2015-06-07T10:41:31.882Z",
    "is_public": false,
    "logo": "default-icon.jpg",
    "is_automated": false,
    "download": 103,
    "upload": 4,
    "pulled_at": "2015-06-07T10:41:31.881Z",
    "pushed_at": "2015-05-24T00:54:26.452Z",
    "is_repo_starred": false
}
```

## List image tags

`GET /v1/repositories/(namespace)/(repo-name)/tags`

**Sample response**:
```json
[
    {
        "image_id": "a4002247cb22e78c8d9ffeccdf7ea23d7763f53493d4d763cb4dbe58bf3566b5",
        "tag": "test"
    },
    {
        "image_id": "e72ac664f4f0c6a061ac4ef332557a70d69b0c62fb6add35f1c181ff7fff2287",
        "tag": "latest"
    }
]
```


## Delete an image repo

`DELETE /v1/repositories/(namespace)/(repo-name)/`


