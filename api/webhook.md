##Create a webhook

`POST /v1/hooks`

```json
{
	"subject_type": "build_repo",
	"subject": "alaudauser/docker_images_test",
	"events": ["build:complete"],
	"secret": "123456",
	"url": "http://example.com:8080/v1/builds",
	"name": "test hook"
}
```

**Parameters**

- **subject_type**: Valid choices: "build_repo", "image_repo"

- **subject**: Path of image/build repo, in the form of <namespace>/<repo_name>

- **events**: Event triggers

- **secret**: Secret key used for digital signatures

- **url**: Callback URL of the webhook

- **name**: Webhook name

**Sample response (status code: 201)**

```json
{
	"id": 4,
	"subject": "alaudauser/build_image_demo",
    "subject_type": "build_repo",
    "events": [
        "build:complete"
    ],
    "name": "test hook",
    "secret": "123456",
    "url": "http://example.com:8080/v1/builds",
    "is_active": true,
    "created_by": "alaudauser",
    "created_at": "2015-08-27T09:53:43.563Z",
    "updated_at": "2015-08-27T09:53:43.566Z"
}
```

##List webhooks

`GET /v1/hooks?subject_type=<subject_type>&subject=<subject>`

**Sample response (status code: 200)**

```json
[
    {
        "id": 4,
        "subject": "alaudadoc/docker_images_test",
        "subject_type": "build_repo",
        "events": [
            "build:complete"
        ],
        "name": "test hook",
        "secret": "123456",
        "url": "http://www.example.com:8080/v1/builds",
        "is_active": true,
        "created_by": "alaudadoc",
        "created_at": "2015-08-27T09:53:43.563Z",
        "updated_at": "2015-08-27T09:53:43.566Z"
    },
    {
       …
       …
    }
]
```

##Retrieve webhook details

`GET /v1/hooks/<hook_id>`

** Sample response (status code: 200)**

```json
{
    "id": 4,
    "subject": "alaudadoc/docker_images_test",
    "subject_type": "build_repo",
    "events": [
        "build:complete"
    ],
    "name": "test hook",
    "secret": "123456",
    "url": "http://www.example.com:8080/v1/builds",
    "is_active": true,
	"created_by": "alaudadoc",
	"created_at": "2015-08-27T09:53:43.563Z",
   	"updated_at": "2015-08-27T09:53:43.566Z"
}
```

##Update a webhook

`PUT /v1/hooks/<hook_id>`

```json
{
	"events": ["build:complete"],
	"secret": "alaudadoc",
	"url": "http://www.example.com:8080/v1/builds",
	"name": "build hook",
	"is_active": false
}
```

**Sample response (status code: 200)**

```json
{
    "id": 4,
    "subject": "alaudadoc/docker_images_test",
    "subject_type": "build_repo",
    "events":
   	[
   	    "build:complete"
    ],
    "name": "build hook",
    "secret": "alaudadoc",
    "url": "http://www.example.com:8080/v1/builds",
    "is_active": true,
    "created_by": "alaudadoc",
    "created_at": "2015-08-27T09:53:43.563Z",
    "updated_at": "2015-08-27T10:02:42.436Z"
}
```

##Delete a webhook

`DELETE /v1/hooks/<hook_id>`

**Sample response (status code: 204)**

