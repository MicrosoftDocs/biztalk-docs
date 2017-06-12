---
title: "Get Instances text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 7b26ddfc-65c5-4a2f-ab8e-9da61d81a1a9
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Instances: text/json
## Get Instances

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Instances

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Instances'|
| Response Body | []|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 02:53:58 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "2",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Id": "string",
    "Class": "string",
    "CreationTime": "2017-04-21T00:56:37.553Z",
    "ErrorDescription": "string",
    "HostName": "string",
    "InstanceStatus": "string",
    "ServiceType": "string",
    "ServiceTypeID": "string",
    "Application": "string",
    "ErrorCode": "string",
    "PendingOperation": "string",
    "MessageBoxServer": "string",
    "MessageBoxDb": "string",
    "ProcessingServer": "string",
    "SuspendTime": "2017-04-21T00:56:37.553Z",
    "Adapter": "string",
    "Uri": "string",
    "PendingJobSubmitTime": "2017-04-21T00:56:37.553Z"
  }
]
```
