---
title: "Get specific SendPortGroup text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 11c2cc95-0179-4891-b207-1a60a65fb7ec
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get specific SendPortGroup: text/json
## Get specific SendPortGroup

  Response Content Type: **text/json**

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


