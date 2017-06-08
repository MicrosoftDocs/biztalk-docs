---
title: "Update Party text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 0b672fe8-2704-49b1-b295-a1388e011daf
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Party: text/xml
## Update Party

  Response Content Type: **text/xml**



Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: text/xml' --header 'Accept: application/json' -d '{partyName}' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D'|
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
  "date": "Tue, 25 Apr 2017 01:39:24 GMT",
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
\<?xml version="1.0"?>
<Party>
  <Id>1</Id>
  <Name>string</Name>
  <Description>string</Description>
  <IsHostPartner>true</IsHostPartner>
  <CertificateName>string</CertificateName>
  <CertificateThumbprint>string</CertificateThumbprint>
  <SendPortNames>string</SendPortNames>
  <Aliases>
    <Name>string</Name>
    <Qualifier>string</Qualifier>
    <Value>string</Value>
    <IsAutoCreated>true</IsAutoCreated>
  </Aliases>
  <BusinessProfiles>string</BusinessProfiles>
  <CustomSettings>
    <Name>string</Name>
    <Value>string</Value>
  </CustomSettings>
</Party>

```

Response Messages
---

HTTP Status Code  | Reason  | Response Model  | Headers
------------- | ------------- | ------------- | -------------
204 | No Content|  |  | 
