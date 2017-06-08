---
title: "GET Pipelines text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 81fcb516-3071-457e-b0f0-d134df81cc48
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Pipelines: text/json
## GET Pipelines

  Response Content Type: **text/json**

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
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Pipelines'|
| Response Body | `[{"FullName":"Microsoft.BizTalk.DefaultPipelines.PassThruReceive","AssemblyQualifiedName":"Microsoft.BizTalk.DefaultPipelines.PassThruReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"Receive","BtsAssembly":"Microsoft.BizTalk.DefaultPipelines","Application":"BizTalk.System","Description":null,"Tracking":{"ServiceStartEnd":true,"MessageSendReceive":true,"InboundMessageBody":false,"OutboundMessageBody":false}},{"FullName":"Microsoft.BizTalk.DefaultPipelines.PassThruTransmit","AssemblyQualifiedName":"Microsoft.BizTalk.DefaultPipelines.PassThruTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"Send","BtsAssembly":"Microsoft.BizTalk.DefaultPipelines","Application":"BizTalk.System","Description":"","Tracking":{"ServiceStartEnd":true,"MessageSendReceive":true,"InboundMessageBody":false,"OutboundMessageBody":false}},{"FullName":"Microsoft.BizTalk.DefaultPipelines.XMLReceive","AssemblyQualifiedName":"Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"Receive","BtsAssembly":"Microsoft.BizTalk.DefaultPipelines","Application":"BizTalk.System","Description":"","Tracking":{"ServiceStartEnd":false,"MessageSendReceive":false,"InboundMessageBody":false,"OutboundMessageBody":false}},{"FullName":"Microsoft.BizTalk.DefaultPipelines.XMLTransmit","AssemblyQualifiedName":"Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"Send","BtsAssembly":"Microsoft.BizTalk.DefaultPipelines","Application":"BizTalk.System","Description":"","Tracking":{"ServiceStartEnd":false,"MessageSendReceive":false,"InboundMessageBody":false,"OutboundMessageBody":false}},{"FullName":"AddDataToSQL.ReceivePipeline1","AssemblyQualifiedName":"AddDataToSQL.ReceivePipeline1, OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0","Type":"Receive","BtsAssembly":"OldOrdersReceive","Application":"OldOrdersReceive","Description":"","Tracking":{"ServiceStartEnd":false,"MessageSendReceive":false,"InboundMessageBody":false,"OutboundMessageBody":false}}]`|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 08:43:43 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "2306",
  "expires": "-1"
}

```

Example Value
---

```
[
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
]
```