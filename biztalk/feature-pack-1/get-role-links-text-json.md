---
title: "Get Role links text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 1d22b40d-ea74-4bf4-9c7f-216d54fa7369
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Role links: text/json
## Get Role links

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/RoleLinks

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/RoleLinks'|
| Response Body | []|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 01:20:43 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "2",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "ServiceLinkType": "string",
    "ApplicationName": "string",
    "AssemblyName": "string",
    "EnlistedParties": [
      {
        "Name": "string",
        "Mappings": [
          {
            "PortTypeName": "string",
            "OperationName": "string",
            "SendPort": "string"
          }
        ]
      }
    ]
  }
]

```
