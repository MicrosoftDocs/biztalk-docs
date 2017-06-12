---
title: "Get details about a specific transform application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 2a2bd6cb-61f4-4b31-a28c-2d6205983685
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get details about a specific transform: application/json
## Get details about a specific transform

  Response Content Type: **application/json**

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
{
  "FullName": "string",
  "ApplicationName": "string",
  "Description": "string",
  "Assembly": "string",
  "SourceSchema": "string",
  "TargetSchema": "string",
  "XmlContent": "string"
}
```


