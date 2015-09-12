## Create a service
`POST /v1/services/(namespace)`

**Sample request**:
```json
{
    "service_name": "test",
    "namespace": "madams",
    "image_name": "index.alauda.cn/alauda/ubuntu",
    "image_tag": "latest",
    "run_command": "",
    "instance_size": "XS",
    "scaling_mode": "MANUAL",
    "target_state": "STARTED",
    "custom_domain_name": "my-own-domain.cn",
    "target_num_instances": 2,
    "instance_envvars":{
        "POSTGRES_USER":"root",
        "POSTGRES_PASSWORD":"123456",
        "PG_HOST": "127.0.0.1",
        "PG_PORT": "5432",
        "REPO_NAME": "pypg2",
        "FILENAME": "scale_with_db"
    },
    "instance_ports":[
        {
            "container_port": 22,
            "protocol": "tcp",
            "endpoint_type": "tcp-endpoint"
        },
        {
            "container_port": 22,
            "protocol": "tcp",
            "endpoint_type": "direct-endpoint"
        }
    ],
    "autoscaling_config": {
        "metric_name" : "CPU_UTILIZATION",
        "metric_stat" : "MEAN",
        "upper_threshold" : "0.6",
        "lower_threshold" : "0.1",
        "decrease_delta" : "1",
        "increase_delta" : "1",
        "minimum_num_instances" : "1",
        "maximum_num_instances" : "6",
        "wait_period" : "30"
    },
    "volumes" : [
        {
            "app_volume_dir" : "/data1",
            "volume_type" : "EBS",
            "size_gb" : 10
        },
        {
            "app_volume_dir" : "/data2",
            "volume_type" : "EBS",
            "size_gb" : 20
        }
    ]
}
```

Parameters:

* **service_name**: - Name of the service
* **namespace**: Username or organization name
* **run_command**: Command to execute when starting the Docker container
* **image_name** Container image name for the service
* **image_tag** Container image tag for the service
* **instance_size**: Container size. Valid choices: "XS", "S", "M", "L", "XL"
* **scaling_mode**: Scaling mode, only applicable to stateless services. Valid choices: "MANUAL", "AUTO"
* **target_state**: Target state of the service after creation. Valid choices: "STARTED", "STOPPED"
* **custom_domain_name**: Custom domain name for the serivce. E.g. "www.myname.com"
* **linked_to_apps**: Links to containers in other services
* **target_num_instances**: Target number of container instances for the service
* **instance_envvars**: Environment variables for the service
* **instance_ports**: Port information for the service
* **autoscaling_config**: Auto-scaling configuration, applicable when the scaling mode is set to AUTO
* **volumes**: Storage volumes


## List services
`GET /v1/services/(namespace)`



**Sample response**:
```json
{
    "count": 2,
    "previous": null,
    "results": [
        {
            "unique_name": "1cd688e2-b4eb-4bf8-9113-5caccdec2db6",
            "service_name": "test",
            "namespace": "madams",
            "updated_at": "2015-04-14T09:46:39.457Z",
            "allocation_group": null,
            "target_state": "STARTED",
            "instance_envvars": "{}",
            "started_at": null,
            "uuid": "1cd688e2-b4eb-4bf8-9113-5caccdec2db6",
            "linked_to_apps": "{}",
            "stopped_at": null,
            "is_deploying": false,
            "created_by": "madams",
            "autoscaling_config": "{}",
            "instance_ports": {},
            "linked_to": "{}",
            "run_command": "",
            "custom_domain_name": "my-own-domain.cn",
            "deployment_preference": "{}",
            "scaling_mode": "MANUAL",
            "image_name": "index.alauda.cn/alauda/ubuntu",
            "image_tag": "latest",
            "instance_size": "XS",
            "linked_from_apps": "{}",
            "target_num_instances": 1,
            "last_autoscaled_at": null,
            "current_num_instances": 1,
            "linked_from": "{}",
            "staged_num_instances": 0,
            "started_num_instances": 1,
            "instances": [
                {
                    "instance_name": "test.0",
                    "started_at": "2015-04-14T09:47:26.895Z",
                    "uuid": "92d03b63-e34b-11e4-9fa4-0240eaf5c02d"
                }
            ],
            "created_at": "2015-04-14T09:46:39.457Z",
            "volumes": [],
            "default_domain_name": "test-madams.alaudacn.me",
            "resource_uri": "/api/v1/apps/test"
        },
        {
            "unique_name": "0cae164e-610c-4a2c-9d36-ff7d2f70054a",
            "service_name": "test1",
            "namespace": "madams",
            "updated_at": "2015-04-14T09:47:09.623Z",
            "target_state": "STARTED",
            "instance_envvars": "{}",
            "started_at": null,
            "uuid": "0cae164e-610c-4a2c-9d36-ff7d2f70054a",
            "linked_to_apps": "{}",
            "stopped_at": null,
            "is_deploying": false,
            "namespace": "madams",
            "created_by": "madams",
            "autoscaling_config": "{}",
            "instance_ports": {},
            "linked_to": "{}",
            "run_command": "",
            "custom_domain_name": "my-own-domain.cn",
            "deployment_preference": "{}",
            "scaling_mode": "MANUAL",
            "image_name": "tutum/ubuntu",
            "image_tag": "latest",
            "instance_size": "XS",
            "linked_from_apps": "{}",
            "target_num_instances": 1,
            "last_autoscaled_at": null,
            "current_num_instances": 1,
            "linked_from": "{}",
            "staged_num_instances": 0,
            "started_num_instances": 1,
            "instances": [
                {
                    "instance_name": "test1.0",
                    "started_at": "2015-04-14T09:47:26.895Z",
                    "uuid": "dcdaadc3-82a6-4ec1-9baa-58f35713626"
                }
            ],
            "created_at": "2015-04-14T09:47:09.623Z",
            "volumes": [
                {
                    "app_volume_dir": "/data/config",
                    "size_gb": 10
                }
            ],
            "default_domain_name": "test1-madams.alaudacn.me",
            "resource_uri": "/api/v1/apps/test1"
        }
    ],
    "next": null
}
```

Parameters:

* **count**: Number of services belonging to the user
* **unique_name**: Unique name assigned to the service
* **updated_at**: Last updated time
* **started_at**: Last started time
* **stopped_at**: Last stopped time
* **is_deploying**: Whether a deployment is in progress for the service
* **namespace**: Username or organization
* **created_by**: User that created the service




## Retrieve service details

`GET /v1/services/(namespace)/(service_name)/`


**Sample response**:
```json
{
    "unique_name": "1cd688e2-b4eb-4bf8-9113-5caccdec2db6",
    "service_name": "test",
    "updated_at": "2015-04-14T09:46:39.457Z",
    "target_state": "STARTED",
    "instance_envvars": "{}",
    "started_at": null,
    "linked_to_apps": "{}",
    "stopped_at": null,
    "is_deploying": false,
    "namespace": "madams",
    "created_by": "madams",
    "autoscaling_config": "{}",
    "instance_ports": {},
    "linked_to": "{}",
    "run_command": "",
    "custom_domain_name": "my-own-domain.cn",
    "deployment_preference": "{}",
    "scaling_mode": "MANUAL",
    "image_name": "index.alauda.cn/alauda/ubuntu",
    "linked_from_apps": "{}",
    "target_num_instances": 1,
    "last_autoscaled_at": null,
    "current_num_instances": 1,
    "linked_from": "{}",
    "staged_num_instances": 0,
    "started_num_instances": 1,
    "instances": [
        {
            "instance_name": "test.0",
            "started_at": "2015-04-14T09:49:56.141Z",
            "uuid": "dcdaadc3-82a6-4ec1-9baa-58f35713626"
        }
    ],
    "created_at": "2015-04-14T09:46:39.457Z",
    "volumes": [],
    "default_domain_name": "test-madams.alaudacn.me",
    "image_tag": "latest",
    "instance_size": "XS",
    "resource_uri": "/api/v1/apps/test"
}
```


## Update a service
`PUT /v1/services/(namespace)/(service-name)/`

**Sample request**:
```json
{
    "service_name": "test",
    "target_num_instances": 3,
    "image_tag":"latest",
    "scaling_mode": "MANUAL"
}
```

## Start a service
`PUT /v1/services/(namespace)/(service-name)/start/`

## Stop a service
`PUT /v1/services/(namespace)/(service-name)/stop/`

## Delete a service
`DELETE /v1/services/(namespace)/(service-name)/`

## Retrieve logs of a service
`GET /v1/services/(namespace)/(service-name)/logs/`

**Sample request**:

`/v1/services/madams/test/logs?start_time=1433753210&end_time=1433753270`


**Sample response**:

```json
[
    {
        "instance_id": "a9aff249",
        "message": "172.31.14.54 - - [12/May/2015 08:47:36] \"GET /alauda.jpg HTTP/1.1\" 200 -",
        "time": 1433753256
    },
    {
        "instance_id": "a9afcb38",
        "message": "172.31.14.54 - - [12/May/2015 08:47:40] \"GET / HTTP/1.1\" 200 -",
        "time": 1433753260
    }
]
```

Parameters:
- **start_time** **end_time**: Retrieve logs within a specific time period
- **instance_id**: ID of the container instance to retrieve logs for
- **message**: Log content
- **time**: Log creation time

