---
title: "Get all maps application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 7376f6c7-1598-454b-83c2-9151317a4ef3
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get all maps: application/json
## Get all maps

  Response Content Type: **application/json**

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
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Transforms' |
| Response Code | 200|

Response body

```
[
  {
    "FullName": "dbo.ConvertToSQLServer",
    "ApplicationName": "OldOrdersReceive",
    "Description": null,
    "Assembly": "dbo.ConvertToSQLServer,OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0",
    "SourceSchema": "AddDataToSQL.Orders",
    "TargetSchema": "AddDataToSQL.TypedProcedure_dbo",
    "XmlContent": "\<?xml version=\"1.0\" encoding=\"UTF-16\"?>\n\<xsl:stylesheet xmlns:xsl=\"http://www.w3.org/1999/XSL/Transform\" xmlns:msxsl=\"urn:schemas-microsoft-com:xslt\" xmlns:var=\"http://schemas.microsoft.com/BizTalk/2003/var\" exclude-result-prefixes=\"msxsl var s0\" version=\"1.0\" xmlns:s0=\"http://AddDataToSQL.Orders\" xmlns:ns0=\"http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo\">\n  \<xsl:output omit-xml-declaration=\"yes\" method=\"xml\" version=\"1.0\" />\n  \<xsl:template match=\"/\">\n    \<xsl:apply-templates select=\"/s0:Order\" />\n  \</xsl:template>\n  \<xsl:template match=\"/s0:Order\">\n    \<ns0:addOldOrders>\n      \<ns0:customerId>\n        \<xsl:value-of select=\"customerId/text()\" />\n      \</ns0:customerId>\n      \<ns0:item>\n        \<xsl:value-of select=\"item/text()\" />\n      \</ns0:item>\n      \<ns0:price>\n        \<xsl:value-of select=\"price/text()\" />\n      \</ns0:price>\n      \<ns0:quantity>\n        \<xsl:value-of select=\"quantity/text()\" />\n      \</ns0:quantity>\n    \</ns0:addOldOrders>\n  \</xsl:template>\n\</xsl:stylesheet>"
  }
]
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 07:33:34 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1387",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "FullName": "string",
    "ApplicationName": "string",
    "Description": "string",
    "Assembly": "string",
    "SourceSchema": "string",
    "TargetSchema": "string",
    "XmlContent": "string"
  }
]

```
