---
title: "Get Details about a specific Pipeline application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 3d2d7db3-a613-46c6-bf05-230f02a1905d
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Details about a specific Pipeline: application/xml
## Get Details about a specific Pipeline

  Response Content Type: **application/xml**

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
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines/%7BpipelineName%7D'|
| Response Body |`<Error>  <Message>Pipeline {pipelineName} does not exist.</Message></Error>` |
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 09:01:02 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "73",
  "expires": "-1"
}
```

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