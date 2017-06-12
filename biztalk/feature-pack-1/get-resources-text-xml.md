---
title: "GET Resources text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 0c785eae-1077-41ca-ac50-5d07883b0e14
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Resources: text/xml
## GET Resources

  Response Content Type: **text/xml**

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
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Resources'|
| Response Body | `<ArrayOfResource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><Resource><Name>Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</Name><Type>System.BizTalk:BizTalkAssembly</Type><ApplicationName>BizTalk.System</ApplicationName></Resource><Resource><Name>Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</Name><Type>System.BizTalk:BizTalkAssembly</Type><ApplicationName>BizTalk.System</ApplicationName></Resource><Resource><Name>Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</Name><Type>System.BizTalk:BizTalkAssembly</Type><ApplicationName>BizTalk.System</ApplicationName></Resource><Resource><Name>MQSeries, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</Name><Type>System.BizTalk:BizTalkAssembly</Type><ApplicationName>BizTalk.System</ApplicationName></Resource><Resource><Name>OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0</Name><Type>System.BizTalk:BizTalkAssembly</Type><ApplicationName>OldOrdersReceive</ApplicationName></Resource></ArrayOfResource>`|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 04:16:39 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1250",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Name>string</Name>
  <Type>string</Type>
  <ApplicationName>string</ApplicationName>
\</Inline Model>
```