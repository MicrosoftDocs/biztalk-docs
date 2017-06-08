---
title: "Get Business profile text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 15405f76-e047-4d7b-aab8-79ee1848cb4a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Business profile: text/json
## Get Business profile

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Parameters
---

Parameter|Value  |Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
partyName|(required)|Party name|path|string| 
profileName|(required)|Profile Name|path|string| 

Example Value
---

```
{
  "Name": "string",
  "Description": "string",
  "BusinessIdentities": [
    {
      "Description": "string",
      "Qualifier": "string",
      "Value": "string",
      "Id": 0
    }
  ],
  "CustomSettings": [
    {
      "Name": "string",
      "Value": "string"
    }
  ]
}
```