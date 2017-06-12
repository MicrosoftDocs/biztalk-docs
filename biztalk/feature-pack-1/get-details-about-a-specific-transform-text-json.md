---
title: "Get details about a specific transform text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c343ec49-cdce-46de-b03a-5352a05bf9eb
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get details about a specific transform: text/json
## Get details about a specific transform

  Response Content Type: **text/json**

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


