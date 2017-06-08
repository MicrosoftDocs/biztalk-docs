---
title: "Get specific SendPortGroup application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 89423da3-ed1f-4ffe-aef8-229204d3cd79
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get specific SendPortGroup: application/json
## Get specific SendPortGroup

  Response Content Type: **application/json**

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
{
  "Name": "string",
  "SendPorts": [
    "string"
  ],
  "CustomData": "string",
  "Filter": "string",
  "Status": "string",
  "ApplicationName": "string",
  "Description": "string"
}
```


