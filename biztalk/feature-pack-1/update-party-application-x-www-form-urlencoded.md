---
title: "Update Party application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 38d74342-146b-4da7-894b-5e14186b6f18
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Party: application/x-www-form-urlencoded
## Update Party

  Response Content Type: **application/x-www-form-urlencoded**


Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' -d '{partyName}' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D'|
| Response Code | 404|

Response Body
---
```
{
  "Message": "Party {partyName} does not exist."
}
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Tue, 25 Apr 2017 02:01:08 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "47",
  "expires": "-1"
}
```
Parameters
---
Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
| **party** | | **Party details** | body | Example Value
| **partyName**  | | **party name** | path | string

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
