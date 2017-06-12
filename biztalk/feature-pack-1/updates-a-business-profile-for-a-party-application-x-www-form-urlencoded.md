---
title: "Updates a business profile for a party application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 12111947-2710-425d-bcb7-4d413e97a89e
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Updates a business profile for a party: application/x-www-form-urlencoded
## Updates a business profile for a party

  Response Content Type: **application/x-www-form-urlencoded**


Parameters
---


Parameter|Value  |Description |Parameter Type|Data Type  
---------|---------|---------|---------|---------
businessProfile|(required)|The business profile.|body|         |
partyName|(required)|Party name.|path|string|
profileName|(required)|Profile name.|path|string|


Response Messages
---

HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204     |No Content|         |         |


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