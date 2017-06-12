---
title: "Get Role link text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 9a55f8fe-6165-40b7-8454-add77179d484
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Role link: text/xml
## Get Role link

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Example Value
---

```
\<?xml version="1.0"?>
<RoleLink>
  <Name>string</Name>
  <ServiceLinkType>string</ServiceLinkType>
  <ApplicationName>string</ApplicationName>
  <AssemblyName>string</AssemblyName>
  <EnlistedParties>
    <Name>string</Name>
    <Mappings>
      <PortTypeName>string</PortTypeName>
      <OperationName>string</OperationName>
      <SendPort>string</SendPort>
    </Mappings>
  </EnlistedParties>
</RoleLink>

```
## Parameters

Parameter  |Value  |Description  |Parameter Type  |Data Type  	
---------|---------|---------|---------|---------| 	
applicationName|  (required)       |        |       path  |  string | 	
roleLinkName|      (required)   |         |       path  |     string | 	
