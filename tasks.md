# API Endpoints

This document lists the APIs to tirgger for task creation and checking task state.

**1. Get all Tasks**

***Request***

`GET http://localhost:8084/applications/{app-name}/tasks?statuses=RUNNING,SUSPENDED,NOT_STARTED`

**2. Get Task Status**

***Request***

`GET http://localhost:8084/tasks/{task-id}`

***Response***

```
{
  "application": "another",
  "buildTime": 1510626921425,
  "endTime": null,
  "execution": {
    "application": "another",
    "authentication": {
      "allowedAccounts": ["phanip", "my-kubernetes-account", "my-docker-registry"],
      "user": "anonymous"
    },
    "buildTime": 1510626921425,
    "canceled": false,
    "canceledBy": null,
    "cancellationReason": null,
    "context": {},
    "description": "Create Load Balancer: another-lb-dt",
    "endTime": null,
    "executionEngine": "v3",
    "id": "83f7e87d-4dc9-4fac-99d2-e9fde9fa01e3",
    "keepWaitingPipelines": false,
    "limitConcurrent": false,
    "name": null,
    "origin": "deck",
    "paused": null,
    "stages": [{
      "context": {
        "account": "my-kubernetes-account",
        "availabilityZones": {
          "default": ["default"]
        },
        "cloudProvider": "kubernetes",
        "clusterIp": "",
        "detail": "dt",
        "externalIps": [],
        "kato.last.task.id": {
          "id": "134"
        },
        "kato.result.expected": true,
        "kato.task.firstNotFoundRetry": -1,
        "kato.task.notFoundRetryCount": 0,
        "kato.tasks": [{
          "history": [{
            "phase": "ORCHESTRATION",
            "status": "Initializing Orchestration Task..."
          }, {
            "phase": "ORCHESTRATION",
            "status": "Processing op: UpsertKubernetesLoadBalancerAtomicOperation"
          }, {
            "phase": "UPSERT_LOAD_BALANCER",
            "status": "Initializing upsert of load balancer another-lb-dt..."
          }, {
            "phase": "UPSERT_LOAD_BALANCER",
            "status": "Looking up provided namespace..."
          }, {
            "phase": "UPSERT_LOAD_BALANCER",
            "status": "Looking up existing load balancer..."
          }],
          "id": "134",
          "resultObjects": [],
          "status": {
            "completed": false,
            "failed": false
          }
        }],
        "loadBalancerIp": "",
        "name": "another-lb-dt",
        "namespace": "default",
        "notification.type": "upsertloadbalancer",
        "ports": [{
          "name": "http",
          "port": 8095,
          "protocol": "TCP"
        }],
        "provider": "kubernetes",
        "refId": "0",
        "requisiteStageRefIds": [],
        "scmInfo": null,
        "serviceAnnotations": {},
        "serviceLabels": {},
        "serviceType": "ClusterIP",
        "sessionAffinity": "None",
        "stack": "lb",
        "stageDetails": {
          "isSynthetic": false,
          "name": "upsertLoadBalancer",
          "startTime": 1510626921443,
          "type": "upsertLoadBalancer"
        },
        "targets": [{
          "availabilityZones": {
            "default": ["default"]
          },
          "credentials": "my-kubernetes-account",
          "name": "another-lb-dt",
          "vpcId": null
        }],
        "user": "anonymous"
      },
      "endTime": null,
      "id": "991aeacd-1041-4e0b-97ae-fd03e4ad75a1",
      "lastModified": null,
      "name": "upsertLoadBalancer",
      "outputs": {},
      "parentStageId": null,
      "refId": "0",
      "requisiteStageRefIds": [],
      "scheduledTime": null,
      "startTime": 1510626921443,
      "status": "RUNNING",
      "syntheticStageOwner": null,
      "tasks": [{
        "endTime": 1510626921546,
        "id": "1",
        "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.loadbalancer.UpsertLoadBalancerTask",
        "loopEnd": false,
        "loopStart": false,
        "name": "upsertLoadBalancer",
        "stageEnd": false,
        "stageStart": true,
        "startTime": 1510626921453,
        "status": "SUCCEEDED"
      }, {
        "endTime": null,
        "id": "2",
        "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.MonitorKatoTask",
        "loopEnd": false,
        "loopStart": false,
        "name": "monitorUpsert",
        "stageEnd": false,
        "stageStart": false,
        "startTime": 1510626921557,
        "status": "RUNNING"
      }, {
        "endTime": null,
        "id": "3",
        "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.loadbalancer.UpsertLoadBalancerResultObjectExtrapolationTask",
        "loopEnd": false,
        "loopStart": false,
        "name": "extrapolateUpsertResult",
        "stageEnd": false,
        "stageStart": false,
        "startTime": null,
        "status": "NOT_STARTED"
      }, {
        "endTime": null,
        "id": "4",
        "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.loadbalancer.UpsertLoadBalancerForceRefreshTask",
        "loopEnd": false,
        "loopStart": false,
        "name": "forceCacheRefresh",
        "stageEnd": true,
        "stageStart": false,
        "startTime": null,
        "status": "NOT_STARTED"
      }],
      "type": "upsertLoadBalancer"
    }],
    "startTime": 1510626921432,
    "status": "RUNNING"
  },
  "id": "83f7e87d-4dc9-4fac-99d2-e9fde9fa01e3",
  "name": "Create Load Balancer: another-lb-dt",
  "startTime": 1510626921432,
  "status": "RUNNING",
  "steps": [{
    "endTime": 1510626921546,
    "id": "1",
    "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.loadbalancer.UpsertLoadBalancerTask",
    "loopEnd": false,
    "loopStart": false,
    "name": "upsertLoadBalancer",
    "stageEnd": false,
    "stageStart": true,
    "startTime": 1510626921453,
    "status": "SUCCEEDED"
  }, {
    "endTime": null,
    "id": "2",
    "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.MonitorKatoTask",
    "loopEnd": false,
    "loopStart": false,
    "name": "monitorUpsert",
    "stageEnd": false,
    "stageStart": false,
    "startTime": 1510626921557,
    "status": "RUNNING"
  }, {
    "endTime": null,
    "id": "3",
    "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.loadbalancer.UpsertLoadBalancerResultObjectExtrapolationTask",
    "loopEnd": false,
    "loopStart": false,
    "name": "extrapolateUpsertResult",
    "stageEnd": false,
    "stageStart": false,
    "startTime": null,
    "status": "NOT_STARTED"
  }, {
    "endTime": null,
    "id": "4",
    "implementingClass": "com.netflix.spinnaker.orca.clouddriver.tasks.loadbalancer.UpsertLoadBalancerForceRefreshTask",
    "loopEnd": false,
    "loopStart": false,
    "name": "forceCacheRefresh",
    "stageEnd": true,
    "stageStart": false,
    "startTime": null,
    "status": "NOT_STARTED"
  }],
  "variables": [{
    "key": "serviceType",
    "value": "ClusterIP"
  }, {
    "key": "serviceLabels",
    "value": {}
  }, {
    "key": "stack",
    "value": "lb"
  }, {
    "key": "externalIps",
    "value": []
  }, {
    "key": "sessionAffinity",
    "value": "None"
  }, {
    "key": "availabilityZones",
    "value": {
      "default": ["default"]
    }
  }, {
    "key": "ports",
    "value": [{
      "name": "http",
      "port": 8095,
      "protocol": "TCP"
    }]
  }, {
    "key": "requisiteStageRefIds",
    "value": []
  }, {
    "key": "provider",
    "value": "kubernetes"
  }, {
    "key": "loadBalancerIp",
    "value": ""
  }, {
    "key": "cloudProvider",
    "value": "kubernetes"
  }, {
    "key": "namespace",
    "value": "default"
  }, {
    "key": "name",
    "value": "another-lb-dt"
  }, {
    "key": "serviceAnnotations",
    "value": {}
  }, {
    "key": "detail",
    "value": "dt"
  }, {
    "key": "refId",
    "value": "0"
  }, {
    "key": "user",
    "value": "anonymous"
  }, {
    "key": "account",
    "value": "my-kubernetes-account"
  }, {
    "key": "clusterIp",
    "value": ""
  }, {
    "key": "stageDetails",
    "value": {
      "isSynthetic": false,
      "name": "upsertLoadBalancer",
      "startTime": 1510626921443,
      "type": "upsertLoadBalancer"
    }
  }, {
    "key": "scmInfo",
    "value": null
  }, {
    "key": "notification.type",
    "value": "upsertloadbalancer"
  }, {
    "key": "kato.result.expected",
    "value": true
  }, {
    "key": "kato.last.task.id",
    "value": {
      "id": "134"
    }
  }, {
    "key": "targets",
    "value": [{
      "availabilityZones": {
        "default": ["default"]
      },
      "credentials": "my-kubernetes-account",
      "name": "another-lb-dt",
      "vpcId": null
    }]
  }, {
    "key": "kato.task.firstNotFoundRetry",
    "value": -1
  }, {
    "key": "kato.task.notFoundRetryCount",
    "value": 0
  }, {
    "key": "kato.tasks",
    "value": [{
      "history": [{
        "phase": "ORCHESTRATION",
        "status": "Initializing Orchestration Task..."
      }, {
        "phase": "ORCHESTRATION",
        "status": "Processing op: UpsertKubernetesLoadBalancerAtomicOperation"
      }, {
        "phase": "UPSERT_LOAD_BALANCER",
        "status": "Initializing upsert of load balancer another-lb-dt..."
      }, {
        "phase": "UPSERT_LOAD_BALANCER",
        "status": "Looking up provided namespace..."
      }, {
        "phase": "UPSERT_LOAD_BALANCER",
        "status": "Looking up existing load balancer..."
      }],
      "id": "134",
      "resultObjects": [],
      "status": {
        "completed": false,
        "failed": false
      }
    }]
  }]
}
```

