---
title: "Get Details about a specific Pipeline text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 3f8a10a4-11a6-4714-92f8-5ead2c11a816
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Details about a specific Pipeline: text/json
## Get Details about a specific Pipeline

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines/%7BpipelineName%7D

Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|pipelineName|{pipelineName}||path|string|

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines/%7BpipelineName%7D'|
| Response Body | `{"Message":"Pipeline {pipelineName} does not exist."}`|
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 08:58:54 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "53",
  "expires": "-1"
}
```

Example Value
---

```
{
  "FullName": "string",
  "AssemblyQualifiedName": "string",
  "Type": "string",
  "BtsAssembly": "string",
  "Application": "string",
  "Description": "string",
  "Tracking": {
    "ServiceStartEnd": true,
    "MessageSendReceive": true,
    "InboundMessageBody": true,
    "OutboundMessageBody": true
  }
}
```