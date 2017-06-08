---
title: "GET Resources text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f8a926e3-eafe-4149-8943-b1dd56601c0c
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Resources: text/json
## GET Resources

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Resources

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Resources'|
| Response Body | ` [{"Name":"Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"System.BizTalk:BizTalkAssembly","ApplicationName":"BizTalk.System"},{"Name":"Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"System.BizTalk:BizTalkAssembly","ApplicationName":"BizTalk.System"},{"Name":"Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"System.BizTalk:BizTalkAssembly","ApplicationName":"BizTalk.System"},{"Name":"MQSeries, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35","Type":"System.BizTalk:BizTalkAssembly","ApplicationName":"BizTalk.System"},{"Name":"OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0","Type":"System.BizTalk:BizTalkAssembly","ApplicationName":"OldOrdersReceive"}] `|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 04:08:24 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "922",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "Type": "string",
    "ApplicationName": "string"
  }
]
```