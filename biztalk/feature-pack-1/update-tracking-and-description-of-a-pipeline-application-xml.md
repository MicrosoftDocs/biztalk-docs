---
title: "Update Tracking and Description of a Pipeline application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 8af5d0bb-e9ab-4e13-b07f-3db3d60c9132
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Tracking and Description of a Pipeline: application/xml
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
\<?xml version="1.0"?>
<Pipeline>
  <FullName>string</FullName>
  <AssemblyQualifiedName>string</AssemblyQualifiedName>
  <Type>string</Type>
  <BtsAssembly>string</BtsAssembly>
  <Application>string</Application>
  <Description>string</Description>
  <Tracking>
    <ServiceStartEnd>true</ServiceStartEnd>
    <MessageSendReceive>true</MessageSendReceive>
    <InboundMessageBody>true</InboundMessageBody>
    <OutboundMessageBody>true</OutboundMessageBody>
  </Tracking>
</Pipeline>

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
| Curl | curl -X PUT --header 'Content-Type: application/xml' --header 'Accept: application/json' -d '{pipelineName}' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines/%7BpipelineName%7D'|
| Response Body | `{  "Message": "Pipeline {pipelineName} does not exist."}`|
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 09:15:03 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "53",
  "expires": "-1"
}
```

