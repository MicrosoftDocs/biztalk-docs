---
title: "Get SendportGroups text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fe40aa36-2adc-4692-b459-88d0910d554d
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get SendportGroups: text/xml
## Get SendportGroups

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  |http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPortGroups |

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPortGroups' |
| Response Code | 200|

## Response Body

```
\<ArrayOfSendPortGroup xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><SendPortGroup><Name>SendPortGroup1</Name><SendPorts><string>BackupFile</string><string>ResponseSQL</string></SendPorts><Filter>&lt;?xml version="1.0" encoding="utf-16"?&gt;
&lt;Filter xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"&gt;
  &lt;Group&gt;
    &lt;Statement Property="BTS.ReceivePortName" Operator="0" Value="RecLoc" /&gt;
  &lt;/Group&gt;
&lt;/Filter&gt;</Filter><Status>Bound</Status><ApplicationName>OldOrdersReceive</ApplicationName></SendPortGroup></ArrayOfSendPortGroup>
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 01:11:39 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "666",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Name>string</Name>
  <SendPorts>string</SendPorts>
  <CustomData>string</CustomData>
  <Filter>string</Filter>
  <Status>string</Status>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
\</Inline Model>

```
