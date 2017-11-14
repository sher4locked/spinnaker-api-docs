## API Endpoints

This document lists the APIs to tirgger for creating and modifying load balancers.

**1. Create a new Load Balancer**

***Request***

`POST ttp://localhost:8084/applications/another/tasks`

```
{
  "job": [{
    "provider": "kubernetes",
    "stack": "lb",
    "detail": "dt",
    "serviceType": "ClusterIP",
    "account": "my-kubernetes-account",
    "namespace": "default",
    "ports": [{
      "protocol": "TCP",
      "port": 8095,
      "name": "http"
    }],
    "externalIps": [],
    "sessionAffinity": "None",
    "clusterIp": "",
    "loadBalancerIp": "",
    "name": "another-lb-dt",
    "serviceAnnotations": {},
    "serviceLabels": {},
    "cloudProvider": "kubernetes",
    "availabilityZones": {
      "default": ["default"]
    },
    "type": "upsertLoadBalancer",
    "user": "anonymous"
  }],
  "application": "another",
  "description": "Create Load Balancer: another-lb-dt"
}
```

***Response***

```
{
  "ref": "/tasks/83f7e87d-4dc9-4fac-99d2-e9fde9fa01e3"
}
```

**2. Get all Load Balancers**

***Request***

`GET http://localhost:8084/applications/another/loadBalancers`

***Response***

```
[{
  "account": "my-kubernetes-account",
  "cloudProvider": "kubernetes",
  "createdTime": 1510626919000,
  "description": {
    "account": "my-kubernetes-account",
    "apiVersion": null,
    "app": "another",
    "clusterIp": "10.110.213.96",
    "credentials": null,
    "detail": "dt",
    "events": [],
    "externalIps": [],
    "kind": null,
    "loadBalancerIp": null,
    "loadBalancerName": null,
    "name": "another-lb-dt",
    "namespace": "default",
    "ports": [{
      "name": "http",
      "nodePort": 0,
      "port": 8095,
      "protocol": "TCP",
      "targetPort": 8095
    }],
    "serviceAnnotations": null,
    "serviceLabels": null,
    "serviceType": "ClusterIP",
    "sessionAffinity": "None",
    "stack": "lb"
  },
  "moniker": {
    "app": "another",
    "cluster": "another-lb-dt",
    "detail": "dt",
    "sequence": null,
    "stack": "lb"
  },
  "name": "another-lb-dt",
  "namespace": "default",
  "region": "default",
  "securityGroups": [],
  "serverGroups": [],
  "service": {
    "apiVersion": "v1",
    "kind": "Service",
    "metadata": {
      "creationTimestamp": "2017-11-14T02:35:19Z",
      "finalizers": [],
      "name": "another-lb-dt",
      "namespace": "default",
      "ownerReferences": [],
      "resourceVersion": "1121693",
      "selfLink": "/api/v1/namespaces/default/services/another-lb-dt",
      "uid": "747e7e48-c8e4-11e7-9b9f-0a556750c1d0"
    },
    "spec": {
      "clusterIP": "10.110.213.96",
      "deprecatedPublicIPs": [],
      "externalIPs": [],
      "loadBalancerSourceRanges": [],
      "ports": [{
        "name": "http",
        "port": 8095,
        "protocol": "TCP",
        "targetPort": 8095
      }],
      "selector": {
        "load-balancer-another-lb-dt": "true"
      },
      "sessionAffinity": "None",
      "type": "ClusterIP"
    },
    "status": {
      "loadBalancer": {
        "ingress": []
      }
    }
  },
  "type": "kubernetes",
  "yaml": "---\napiVersion: \"v1\"\nkind: \"Service\"\nmetadata:\n  finalizers: []\n  name: \"another-lb-dt\"\n  namespace: \"default\"\n  ownerReferences: []\nspec:\n  clusterIP: \"10.110.213.96\"\n  deprecatedPublicIPs: []\n  externalIPs: []\n  loadBalancerSourceRanges: []\n  ports:\n  - name: \"http\"\n    port: 8095\n    protocol: \"TCP\"\n    targetPort: 8095\n  selector:\n    load-balancer-another-lb-dt: \"true\"\n  sessionAffinity: \"None\"\n  type: \"ClusterIP\"\nstatus:\n  loadBalancer:\n    ingress: []\n"
}]
```

