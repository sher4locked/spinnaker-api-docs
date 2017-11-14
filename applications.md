## API Endpoints

This document lists the APIs to tirgger for application creation and checking application state.

**1. Create a new Application**

***Request***

`POST http://localhost:8084/applications/{app-name}/tasks`

```
{
  "job": [{
    "type": "createApplication",
    "application": {
      "cloudProviders": "kubernetes",
      "instancePort": 80,
      "providerSettings": {
        "aws": {
          "useAmiBlockDeviceMappings": false
        }
      },
      "name": "{app-name}",
      "email": "gen@email.com"
    },
    "user": "anonymous"
  }],
  "application": "another",
  "description": "Create Application: app-name"
}
```

***Response***

```
{
  "ref": "/tasks/5b459e90-f367-44bf-8d4c-989ce0032faa"
}
```

**2. Get Application Status**

***Request***

`GET http://localhost:8084/applications/{app-name}`

***Response***

```
{
  "attributes": {
    "accounts": null,
    "cloudProviders": "kubernetes",
    "createTs": "1510622522379",
    "email": "anush@opsmx.com",
    "instancePort": 80,
    "lastModifiedBy": "anonymous",
    "name": "another",
    "providerSettings": {
      "aws": {
        "useAmiBlockDeviceMappings": false
      }
    },
    "updateTs": "1510622520000",
    "user": "anonymous"
  },
  "clusters": {},
  "name": "another"
}
```
