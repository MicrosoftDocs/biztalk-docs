---
title: "Get specific SendPortGroup text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 66bc8d4d-75f2-43b1-81b3-6908f630dbca
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get specific SendPortGroup: text/xml
## Get specific SendPortGroup

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

## *Parameters*	
Parameter  |Value  |Description  |Parameter Type  |Data Type  	
---------|---------|---------|---------|---------| 	
sendPortGroupName|  (required)       |    Name of SendPortGroup    |       path  |  string | 	

## Example Value


```
\<?xml version="1.0"?>
<SendPortGroup>
  <Name>string</Name>
  <SendPorts>string</SendPorts>
  <CustomData>string</CustomData>
  <Filter>string</Filter>
  <Status>string</Status>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
</SendPortGroup>
```


