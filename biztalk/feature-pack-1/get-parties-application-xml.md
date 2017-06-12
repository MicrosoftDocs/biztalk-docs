---
title: "Get Parties application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: dffaf248-b725-4f32-be22-de28008e24a2
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Parties: application/xml
## Get Parties

  Response Content Type: **application/xml**

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
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties'|
| Response Code | 200|


Response Body
---
```
<ArrayOfParty xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" />
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 08:37:06 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "115",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
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
\</Inline Model>
```
