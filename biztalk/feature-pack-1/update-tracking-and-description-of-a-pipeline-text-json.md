---
title: "Update Tracking and Description of a Pipeline text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 0ddae969-9db4-46c7-b044-4d44ae2b53bd
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Tracking and Description of a Pipeline: text/json
## Update Tracking and Description of a Pipeline


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|pipelineName|{pipelineName}|Name of pipeline to be updated|path|string|
|pipeline|{pipelineName}|Pipeline details|body|Example Value|

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

Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines/%7BpipelineName%7D

Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||

Response
---
| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: text/json' --header 'Accept: application/json' -d '{pipelineName}' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines/%7BpipelineName%7D'|
| Response Body | `{  "Message": "Pipeline {pipelineName} does not exist."}`|
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 09:13:08 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "53",
  "expires": "-1"
}
```

