This document lists the APIs to tirgger for cluster creation and checking cluster creation state.

**1. Find Images from Docker Repository**

***Request***

`GET http://localhost:8084/images/find?count=50&provider=dockerRegistry&q=gs-rest-service:latest`

***Response***

```
[{
  "account": "my-docker-registry",
  "artifact": {
    "metadata": {
      "registry": "quay.io"
    },
    "name": "veerendra2/gs-rest-service",
    "reference": "quay.io/veerendra2/gs-rest-service:latest",
    "type": "docker",
    "version": "latest"
  },
  "registry": "quay.io",
  "repository": "veerendra2/gs-rest-service",
  "tag": "latest"
}]
```

**2. Create a new Cluster**

***Request***

`POST http://localhost:8084/applications/another/tasks`

```
{
  "job": [{
    "account": "my-kubernetes-account",
    "application": "another",
    "strategy": "",
    "targetSize": 1,
    "cloudProvider": "kubernetes",
    "namespace": "default",
    "containers": [{
      "name": "veerendra2-gs-rest-service",
      "imageDescription": {
        "repository": "veerendra2/gs-rest-service",
        "tag": "latest",
        "imageId": "quay.io/veerendra2/gs-rest-service:latest",
        "registry": "quay.io",
        "account": "my-docker-registry"
      },
      "imagePullPolicy": "IFNOTPRESENT",
      "requests": {
        "memory": null,
        "cpu": null
      },
      "limits": {
        "memory": null,
        "cpu": null
      },
      "ports": [{
        "name": "http",
        "containerPort": 8095,
        "protocol": "TCP",
        "hostPort": null,
        "hostIp": null
      }],
      "livenessProbe": null,
      "readinessProbe": null,
      "envVars": [],
      "command": [],
      "args": [],
      "volumeMounts": []
    }],
    "volumeSources": [],
    "terminationGracePeriodSeconds": 30,
    "deployment": {
      "enabled": false,
      "minReadySeconds": 0,
      "deploymentStrategy": {
        "type": "RollingUpdate",
        "rollingUpdate": {
          "maxUnavailable": 1,
          "maxSurge": 1
        }
      }
    },
    "interestingHealthProviderNames": ["KubernetesContainer", "KubernetesPod"],
    "dnsPolicy": "ClusterFirst",
    "replicaSetAnnotations": {},
    "podAnnotations": {},
    "nodeSelector": {},
    "stack": "clstr",
    "freeFormDetails": "dt",
    "loadBalancers": ["another-lb-dt"],
    "type": "createServerGroup",
    "region": "default",
    "user": "anonymous"
  }],
  "application": "another",
  "description": "Create New Server Group in cluster another-clstr-dt"
}
```

***Response***

```
{
  "ref": "/tasks/b4594afa-32ff-46aa-94a8-a481fb62b1cf"
}
```


