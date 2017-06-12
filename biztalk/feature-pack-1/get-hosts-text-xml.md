---
title: "Get hosts text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 76ee833d-c07e-41c1-9150-61c2d3758d4a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get hosts: text/xml
## Get hosts

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Hosts

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Hosts'|
| Response Code | 200|

Response Body
---
```
<ArrayOfHost xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><Host><Name>SendHost</Name><IsDefault>true</IsDefault><NTGroupName>BizTalk Application Users</NTGroupName><Type>InProcess</Type><IsTrusted>false</IsTrusted></Host><Host><Name>BizTalkServerIsolatedHost</Name><IsDefault>false</IsDefault><NTGroupName>BizTalk Isolated Host Users</NTGroupName><Type>Isolated</Type><IsTrusted>false</IsTrusted></Host><Host><Name>ProcessingHost</Name><IsDefault>false</IsDefault><NTGroupName>BizTalk Application Users</NTGroupName><Type>InProcess</Type><IsTrusted>false</IsTrusted></Host><Host><Name>ReceiveHost</Name><IsDefault>false</IsDefault><NTGroupName>BizTalk Application Users</NTGroupName><Type>InProcess</Type><IsTrusted>false</IsTrusted></Host><Host><Name>TrackingHost</Name><IsDefault>false</IsDefault><NTGroupName>BizTalk Application Users</NTGroupName><Type>InProcess</Type><IsTrusted>false</IsTrusted></Host></ArrayOfHost>
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 02:10:42 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "976",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Name>string</Name>
  <IsDefault>true</IsDefault>
  <NTGroupName>string</NTGroupName>
  <Type>string</Type>
  <IsTrusted>true</IsTrusted>
\</Inline Model>
```