This document lists the APIs to trigger to create a pipeline, modify pipeline config and add stages to pipelines.

**1. Create a new Pipeline**

***Request***

`POST http://localhost:8084/pipelines`

```
{
  "name": "pipe",
  "stages": [],
  "triggers": [],
  "application": "another",
  "limitConcurrent": true,
  "keepWaitingPipelines": false,
  "index": 0
}
```

***Response***

```
{
  "ref": "/tasks/5b459e90-f367-44bf-8d4c-989ce0032faa"
}
```

**2. Add a stage to a Pipeline**

***Request***

`POST http://localhost:8084/pipelines`

```
{
  "application": "another",
  "id": "578ab794-28b7-4395-aa68-ca3e20f9739e",
  "index": 0,
  "keepWaitingPipelines": false,
  "lastModifiedBy": "anonymous",
  "limitConcurrent": true,
  "name": "pipe",
  "stages": [{
    "refId": "1",
    "requisiteStageRefIds": [],
    "type": "acaTask",
    "name": "ACA Task",
    "baseline": {},
    "canary": {
      "application": "another",
      "owner": "anonymous",
      "watchers": [],
      "canaryConfig": {
        "name": "veeru123",
        "canaryHealthCheckHandler": {
          "@class": "com.netflix.spinnaker.mine.CanaryResultHealthCheckHandler",
          "minimumCanaryResultScore": "55"
        },
        "canaryAnalysisConfig": {
          "notificationHours": [],
          "useLookback": false,
          "lookbackMins": 0,
          "name": "veeru",
          "beginCanaryAnalysisAfterMins": "3",
          "canaryAnalysisIntervalMins": "12"
        },
        "lifetimeHours": "0.25",
        "combinedCanaryResultStrategy": "AGGREGATE",
        "canarySuccessCriteria": {
          "canaryResultScore": "75"
        }
      },
      "canaryDeployments": [{
        "type": "cluster",
        "@class": ".CanaryTaskDeployment",
        "accountName": "my-kubernetes-account",
        "baseline": "another-clstr-dt-v000",
        "canary": "another-clstr-dt-current"
      }]
    }
  }],
  "triggers": [],
  "updateTs": "1510628989000"
}
```

The above request is an example of adding an ACA task to the pipeline.

**3. Get Pipeline Configuration**

***Resquest***

`GET http://localhost:8084/applications/another/pipelineConfigs`

***Response***

```
[{
  "application": "another",
  "id": "578ab794-28b7-4395-aa68-ca3e20f9739e",
  "index": 0,
  "keepWaitingPipelines": false,
  "lastModifiedBy": "anonymous",
  "limitConcurrent": true,
  "name": "pipe",
  "stages": [{
    "baseline": {},
    "canary": {
      "application": "another",
      "canaryConfig": {
        "canaryAnalysisConfig": {
          "beginCanaryAnalysisAfterMins": "3",
          "canaryAnalysisIntervalMins": "12",
          "lookbackMins": 0,
          "name": "veeru",
          "notificationHours": [],
          "useLookback": false
        },
        "canaryHealthCheckHandler": {
          "@class": "com.netflix.spinnaker.mine.CanaryResultHealthCheckHandler",
          "minimumCanaryResultScore": "55"
        },
        "canarySuccessCriteria": {
          "canaryResultScore": "75"
        },
        "combinedCanaryResultStrategy": "AGGREGATE",
        "lifetimeHours": "0.25",
        "name": "veeru123"
      },
      "canaryDeployments": [{
        "@class": ".CanaryTaskDeployment",
        "accountName": "my-kubernetes-account",
        "baseline": "another-clstr-dt-v000",
        "canary": "another-clstr-dt-current",
        "type": "cluster"
      }],
      "owner": "anonymous",
      "watchers": []
    },
    "name": "ACA Task",
    "refId": "1",
    "requisiteStageRefIds": [],
    "type": "acaTask"
  }],
  "triggers": [],
  "updateTs": "1510631186000"
}]
```

