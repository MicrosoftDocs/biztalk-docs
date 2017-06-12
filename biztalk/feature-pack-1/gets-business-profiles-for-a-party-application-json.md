---
title: "Gets business profiles for a Party application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ed6e6d19-6bb4-4cfd-8644-c1d1b2c8e48a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Gets business profiles for a Party: application/json
## Gets business profiles for a Party

  Response Content Type: **application/json**

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