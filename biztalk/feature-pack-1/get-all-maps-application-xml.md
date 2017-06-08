---
title: "Get all maps application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c216093e-f0d2-4d50-9d61-730413cb6571
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get all maps: application/xml
## Get all maps

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  |http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Transforms |

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Transforms' |
| Response Code | 200|

## Response Body


```
\<ArrayOfTransform xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <Transform>
    <FullName>dbo.ConvertToSQLServer</FullName>
    <ApplicationName>OldOrdersReceive</ApplicationName>
    <Assembly>dbo.ConvertToSQLServer,OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0</Assembly>
    <SourceSchema>AddDataToSQL.Orders</SourceSchema>
    <TargetSchema>AddDataToSQL.TypedProcedure_dbo</TargetSchema>
    <XmlContent>
      &lt;?xml version="1.0" encoding="UTF-16"?&gt;
      &lt;xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:var="http://schemas.microsoft.com/BizTalk/2003/var" exclude-result-prefixes="msxsl var s0" version="1.0" xmlns:s0="http://AddDataToSQL.Orders" xmlns:ns0="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo"&gt;
        &lt;xsl:output omit-xml-declaration="yes" method="xml" version="1.0" /&gt;
        &lt;xsl:template match="/"&gt;
          &lt;xsl:apply-templates select="/s0:Order" /&gt;
        &lt;/xsl:template&gt;
        &lt;xsl:template match="/s0:Order"&gt;
          &lt;ns0:addOldOrders&gt;
            &lt;ns0:customerId&gt;
              &lt;xsl:value-of select="customerId/text()" /&gt;
            &lt;/ns0:customerId&gt;
            &lt;ns0:item&gt;
              &lt;xsl:value-of select="item/text()" /&gt;
            &lt;/ns0:item&gt;
            &lt;ns0:price&gt;
              &lt;xsl:value-of select="price/text()" /&gt;
            &lt;/ns0:price&gt;
            &lt;ns0:quantity&gt;
              &lt;xsl:value-of select="quantity/text()" /&gt;
            &lt;/ns0:quantity&gt;
          &lt;/ns0:addOldOrders&gt;
        &lt;/xsl:template&gt;
    &lt;/xsl:stylesheet&gt;</XmlContent>
  </Transform>
</ArrayOfTransform>
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 07:49:00 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1683",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <FullName>string</FullName>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
  <Assembly>string</Assembly>
  <SourceSchema>string</SourceSchema>
  <TargetSchema>string</TargetSchema>
  <XmlContent>string</XmlContent>
\</Inline Model>

```
