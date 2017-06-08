---
title: "Add a party alias text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 44109fc9-d105-4b7c-b46e-86c72564224a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Add a party alias: text/xml
## Add a party alias

  Response Content Type: **text/xml**



Method  | Request URL
------------- | -------------
POST  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X POST --header 'Content-Type: text/xml' --header 'Accept: application/json' -d '{partyName}' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D'|
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
  "date": "Tue, 25 Apr 2017 01:14:44 GMT",
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
| **partyAlias** | | **Party Alias details** | body | Example Value
| **partyName**  | | **Party Name** | path | string

Example Value
---

```
\<?xml version="1.0"?>
<PartyAlias>
  <Name>string</Name>
  <Qualifier>string</Qualifier>
  <Value>string</Value>
  <IsAutoCreated>true</IsAutoCreated>
</PartyAlias>
```

Response Messages
---

HTTP Status Code  | Reason  | Response Model  | Headers
------------- | ------------- | ------------- | -------------
204 | No Content|  |  | 
