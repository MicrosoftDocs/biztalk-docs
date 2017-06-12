---
title: "GET Pipelines text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 251805fa-6c6b-4628-9555-3b57de0e61d0
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Pipelines: text/xml
## GET Pipelines

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines'|
| Response Body |`<ArrayOfPipeline xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><Pipeline><FullName>Microsoft.BizTalk.DefaultPipelines.PassThruReceive</FullName><AssemblyQualifiedName>Microsoft.BizTalk.DefaultPipelines.PassThruReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</AssemblyQualifiedName><Type>Receive</Type><BtsAssembly>Microsoft.BizTalk.DefaultPipelines</BtsAssembly><Application>BizTalk.System</Application><Tracking><ServiceStartEnd>true</ServiceStartEnd><MessageSendReceive>true</MessageSendReceive><InboundMessageBody>false</InboundMessageBody><OutboundMessageBody>false</OutboundMessageBody></Tracking></Pipeline><Pipeline><FullName>Microsoft.BizTalk.DefaultPipelines.PassThruTransmit</FullName><AssemblyQualifiedName>Microsoft.BizTalk.DefaultPipelines.PassThruTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</AssemblyQualifiedName><Type>Send</Type><BtsAssembly>Microsoft.BizTalk.DefaultPipelines</BtsAssembly><Application>BizTalk.System</Application><Description /><Tracking><ServiceStartEnd>true</ServiceStartEnd><MessageSendReceive>true</MessageSendReceive><InboundMessageBody>false</InboundMessageBody><OutboundMessageBody>false</OutboundMessageBody></Tracking></Pipeline><Pipeline><FullName>Microsoft.BizTalk.DefaultPipelines.XMLReceive</FullName><AssemblyQualifiedName>Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</AssemblyQualifiedName><Type>Receive</Type><BtsAssembly>Microsoft.BizTalk.DefaultPipelines</BtsAssembly><Application>BizTalk.System</Application><Description /><Tracking><ServiceStartEnd>false</ServiceStartEnd><MessageSendReceive>false</MessageSendReceive><InboundMessageBody>false</InboundMessageBody><OutboundMessageBody>false</OutboundMessageBody></Tracking></Pipeline><Pipeline><FullName>Microsoft.BizTalk.DefaultPipelines.XMLTransmit</FullName><AssemblyQualifiedName>Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</AssemblyQualifiedName><Type>Send</Type><BtsAssembly>Microsoft.BizTalk.DefaultPipelines</BtsAssembly><Application>BizTalk.System</Application><Description /><Tracking><ServiceStartEnd>false</ServiceStartEnd><MessageSendReceive>false</MessageSendReceive><InboundMessageBody>false</InboundMessageBody><OutboundMessageBody>false</OutboundMessageBody></Tracking></Pipeline><Pipeline><FullName>AddDataToSQL.ReceivePipeline1</FullName><AssemblyQualifiedName>AddDataToSQL.ReceivePipeline1, OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0</AssemblyQualifiedName><Type>Receive</Type><BtsAssembly>OldOrdersReceive</BtsAssembly><Application>OldOrdersReceive</Application><Description /><Tracking><ServiceStartEnd>false</ServiceStartEnd><MessageSendReceive>false</MessageSendReceive><InboundMessageBody>false</InboundMessageBody><OutboundMessageBody>false</OutboundMessageBody></Tracking></Pipeline></ArrayOfPipeline>` |
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 08:51:18 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "3167",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
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
\</Inline Model>
```