---
title: "Get Instances application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 471debf9-ff61-460a-ab4b-b7a671e8bac9
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Instances: application/json
## Get Instances

  Response Content Type: **application/json**

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
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Instances'|
| Response Body | []|
| Response Code | 200|


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 02:50:05 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
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
