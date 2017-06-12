---
title: "Create Party application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fe001aba-590c-44f1-9a2b-c08c23ba1224
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create Party: application/xml
## Create Party

  Response Content Type: **application/xml**



Method  | Request URL
------------- | -------------
POST  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X POST --header 'Content-Type: application/xml' --header 'Accept: text/plain' -d 'Parties' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Parties'|
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
  "date": "Mon, 24 Apr 2017 08:56:20 GMT",
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
