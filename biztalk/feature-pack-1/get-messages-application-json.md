---
title: "Get Messages application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 11d7f87f-cc83-49b9-8e00-36f7b14f37f5
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Messages: application/json
## Get Messages

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Messages

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Messages'|
| Response Body | []|
| Response Code | 200|


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 05:53:40 GMT",
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
    "Adapter": "string",
    "CreationTime": "2017-04-21T00:56:37.566Z",
    "HostName": "string",
    "MessageBoxDB": "string",
    "MessageBoxServer": "string",
    "MessageID": "string",
    "MessageType": "string",
    "OriginatorPartyName": "string",
    "OriginatorSecurityName": "string",
    "RetryCount": 0,
    "ServiceClass": "string",
    "ServiceInstanceID": "string",
    "ServiceName": "string",
    "ServiceStatus": "string",
    "ServiceTypeID": "string",
    "Status": "string",
    "Submitter": "string",
    "URI": "string"
  }
]

```
