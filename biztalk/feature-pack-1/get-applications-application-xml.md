---
title: "GET Applications application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: aac4f92c-0048-43e1-b92a-db444b03b9f7
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Applications: application/xml
## GET Applications

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Applications'|
 Response Body  
 
```
\<ArrayOfApplication xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <Application>
    <Name>BizTalk.System</Name>
    <Description>System Application</Description>
    <IsDefaultApplication>false</IsDefaultApplication>
    <IsSystem>true</IsSystem>
    <Status>NotApplicable</Status>
    <IsConfigured>true</IsConfigured>
    <ApplicationReferences />
    <ApplicationBackReferences>
      <string>BizTalk Application 1</string>
      <string>OldOrdersReceive</string>
    </ApplicationBackReferences>
  </Application>
  <Application>
    <Name>BizTalk Application 1</Name>
    <Description>BizTalk Application 1</Description>
    <IsDefaultApplication>true</IsDefaultApplication>
    <IsSystem>false</IsSystem>
    <Status>NotApplicable</Status>
    <IsConfigured>true</IsConfigured>
    <ApplicationReferences>
      <string>BizTalk.System</string>
    </ApplicationReferences>
    <ApplicationBackReferences />
  </Application>
  <Application>
    <Name>OldOrdersReceive</Name>
    <IsDefaultApplication>false</IsDefaultApplication>
    <IsSystem>false</IsSystem>
    <Status>PartiallyStarted</Status>
    <IsConfigured>true</IsConfigured>
    <ApplicationReferences>
      <string>BizTalk.System</string>
    </ApplicationReferences>
    <ApplicationBackReferences />
  </Application>
</ArrayOfApplication>
```

 Response Code  200

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 02:19:05 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1187",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Name>string</Name>
  <Description>string</Description>
  <IsDefaultApplication>true</IsDefaultApplication>
  <IsSystem>true</IsSystem>
  <Status>string</Status>
  <IsConfigured>true</IsConfigured>
  <ApplicationReferences>string</ApplicationReferences>
  <ApplicationBackReferences>string</ApplicationBackReferences>
\</Inline Model>
```