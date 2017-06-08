---
title: "Get details about a specific transform text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: eb917dfd-386b-4994-9182-9db32e063106
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get details about a specific transform: text/xml
## Get details about a specific transform

  Response Content Type: **text/xml**

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


