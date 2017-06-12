---
title: "Get hosts application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c469027a-9b05-4839-bc9f-1ddec5aca83f
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get hosts: application/json
## Get hosts

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Hosts

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Hosts'|
| Response Code | 200|


Response Body
---
```
[
  {
    "Name": "SendHost",
    "IsDefault": true,
    "NTGroupName": "BizTalk Application Users",
    "Type": "InProcess",
    "IsTrusted": false
  },
  {
    "Name": "BizTalkServerIsolatedHost",
    "IsDefault": false,
    "NTGroupName": "BizTalk Isolated Host Users",
    "Type": "Isolated",
    "IsTrusted": false
  },
  {
    "Name": "ProcessingHost",
    "IsDefault": false,
    "NTGroupName": "BizTalk Application Users",
    "Type": "InProcess",
    "IsTrusted": false
  },
  {
    "Name": "ReceiveHost",
    "IsDefault": false,
    "NTGroupName": "BizTalk Application Users",
    "Type": "InProcess",
    "IsTrusted": false
  },
  {
    "Name": "TrackingHost",
    "IsDefault": false,
    "NTGroupName": "BizTalk Application Users",
    "Type": "InProcess",
    "IsTrusted": false
  }
]
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 01:00:49 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "616",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "IsDefault": true,
    "NTGroupName": "string",
    "Type": "string",
    "IsTrusted": true
  }
]

```
