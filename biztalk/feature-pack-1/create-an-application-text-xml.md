---
title: "Create an Application text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 1280a306-b626-4597-aa98-474794c235e6
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create an Application: text/xml
## Create an Application

  Response Content Type: **text/xml**
  
Parameters
---



Parameter |Value |Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
application  |         |Details of Application to be created |body |        |


Response Messages
---


HTTP Status Code|Reason  |Response Model|Headers
---------|---------|---------|---------
204    |No Content       |         |         |

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X POST --header 'Content-Type: text/xml' --header 'Accept: application/json' -d ' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications'|
| Response Body | { "Message": "Application with name string exists." }|
| Response Code | 409|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 07:41:36 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "50",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Application>
  <Name>string</Name>
  <Description>string</Description>
  <IsDefaultApplication>true</IsDefaultApplication>
  <IsSystem>true</IsSystem>
  <Status>string</Status>
  <IsConfigured>true</IsConfigured>
  <ApplicationReferences>string</ApplicationReferences>
  <ApplicationBackReferences>string</ApplicationBackReferences>
</Application>

```
