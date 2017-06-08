---
title: "Get Parties application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 05fd2022-4523-4cd7-aca8-bd3a97cb642f
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Parties: application/json
## Get Parties

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties'|
| Response Body | []|
| Response Code | 200|



Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 08:26:48 GMT",
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
    "Id": 0,
    "Name": "string",
    "Description": "string",
    "IsHostPartner": true,
    "CertificateName": "string",
    "CertificateThumbprint": "string",
    "SendPortNames": [
      "string"
    ],
    "Aliases": [
      {
        "Name": "string",
        "Qualifier": "string",
        "Value": "string",
        "IsAutoCreated": true
      }
    ],
    "BusinessProfiles": [
      "string"
    ],
    "CustomSettings": [
      {
        "Name": "string",
        "Value": "string"
      }
    ]
  }
]

```
