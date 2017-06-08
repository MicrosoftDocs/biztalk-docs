---
title: "Get Business profile application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: b38b5b88-ec26-4249-ab57-5d5b4063ce7c
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Business profile: application/json
## Get Business profile

  Response Content Type: **application/json**

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