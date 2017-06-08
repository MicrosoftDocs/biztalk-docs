---
title: "Create an Application application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 21e9672f-3db9-4a4e-be77-fd5c72b3aed0
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create an Application: application/xml
## Create an Application

  Response Content Type: **application/xml**
  
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
| Curl | curl -X POST --header 'Content-Type: application/xml' --header 'Accept: application/json' -d 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications'|
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
