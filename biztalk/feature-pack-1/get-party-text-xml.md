---
title: "Get Party text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f39a8db5-bae2-4880-b558-d9f63cf794cd
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Party: text/xml
## Get Party

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties/%7BpartyName%7D'|
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
  "date": "Mon, 24 Apr 2017 09:27:45 GMT",
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
**partyName** | | **party name** | path | string

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