---
title: "Gets business profiles for a Party text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 7adca50c-d5f4-4c9c-aeee-3eb6570698a9
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Gets business profiles for a Party: text/json
## Gets business profiles for a Party

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Parameters
---


Parameter|Value|Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
partyName|(required)|Party name|path|string|

Example Value
---

```
[
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
]
```