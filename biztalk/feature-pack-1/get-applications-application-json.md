---
title: "GET Applications application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 600e5b4b-ac02-4073-80f1-8c58b203be78
caps.latest.revision: 4
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Applications: application/json
## GET Applications

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications'|
 Response Body
 
```
[
  {
    "Name": "BizTalk.System",
    "Description": "System Application",
    "IsDefaultApplication": false,
    "IsSystem": true,
    "Status": "NotApplicable",
    "IsConfigured": true,
    "ApplicationReferences": [],
    "ApplicationBackReferences": [
      "BizTalk Application 1",
      "OldOrdersReceive"
    ]
  },
  {
    "Name": "BizTalk Application 1",
    "Description": "BizTalk Application 1",
    "IsDefaultApplication": true,
    "IsSystem": false,
    "Status": "NotApplicable",
    "IsConfigured": true,
    "ApplicationReferences": [
      "BizTalk.System"
    ],
    "ApplicationBackReferences": []
  },
  {
    "Name": "OldOrdersReceive",
    "Description": null,
    "IsDefaultApplication": false,
    "IsSystem": false,
    "Status": "PartiallyStarted",
    "IsConfigured": true,
    "ApplicationReferences": [
      "BizTalk.System"
    ],
    "ApplicationBackReferences": []
  }
]
```
  
 Response Code  200

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 01:32:52 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "702",
  "expires": "-1"
}
```

Example Value
---

```
[
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
]
```
