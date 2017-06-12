---
title: "Create Party application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: dd4b2314-2b19-41e2-87a8-aeb49fbdc2c9
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create Party: application/json
## Create Party

  Response Content Type: **application/json**


Method  | Request URL
------------- | -------------
POST  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X POST --header 'Content-Type: application/json' --header 'Accept: text/plain' -d 'Parties' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties'|
| Response Code | 500|


Response Body
---
```
Object reference not set to an instance of an object.
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 08:49:06 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "53",
  "expires": "-1"
}
```
Parameters
---
Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
**party** | | **Party details** | body | Example Value

Example Value
---
```
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
```
Response Messages
---

HTTP Status Code  | Reason  | Response Model  | Headers
------------- | ------------- | ------------- | -------------
204 | No Content|  |  | 

