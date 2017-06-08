---
title: "Get details about a specific transform application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c7b23c75-26cc-44a2-ab08-c7c7e36674d8
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get details about a specific transform: application/xml
## Get details about a specific transform

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK


## *Parameters*	
Parameter  |Value  |Description  |Parameter Type  |Data Type  	
---------|---------|---------|---------|---------| 	
**transformFullName**|  (required)       |  Full name of the transform      |       path  |  string | 	


## Example Value


```
\<?xml version="1.0"?>
<Transform>
  <FullName>string</FullName>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
  <Assembly>string</Assembly>
  <SourceSchema>string</SourceSchema>
  <TargetSchema>string</TargetSchema>
  <XmlContent>string</XmlContent>
</Transform>
```


