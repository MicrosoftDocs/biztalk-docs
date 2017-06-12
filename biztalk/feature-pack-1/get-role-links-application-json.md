---
title: "Get Role links application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 5eed3eab-ab0b-4b96-aeff-34d4fd1efabb
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Role links: application/json
## Get Role links

  Response Content Type: **application/json**

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
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/RoleLinks'|
| Response Body | []|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 01:10:43 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
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
