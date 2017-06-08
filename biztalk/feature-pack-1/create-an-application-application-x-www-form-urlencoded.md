---
title: "Create an Application application x-www-form-urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e083785d-b5ad-40eb-9328-e3030ccdc247
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create an Application: application/x-www-form-urlencoded
## Create an Application

  Response Content Type: **application/x-www-form-urlencoded**
  
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
| Curl | curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' -d 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications'|
| Response Body | { "Message": "Application Name not specified in the input" }|
| Response Code | 400|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 07:54:08 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "57",
  "expires": "-1"
}
```

Example Value
---

```
{
  "Name": "string",
  "Description": "string",
  "IsDefaultApplication": true,
  "IsSystem": true,
  "Status": "string",
  "IsConfigured": true,
  "ApplicationReferences": [
    "string"
  ],
  "ApplicationBackReferences": [
    "string"
  ]
}
```
