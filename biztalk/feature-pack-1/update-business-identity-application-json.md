---
title: "Update business identity application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ac28535d-e8e0-4a3b-a1a6-af088ab6ec0e
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update business identity: application/json
## Update business identity

  Response Content Type: **application/json**

Parameters
---


Parameter|Value  |Description |Parameter Type|Data Type  
---------|---------|---------|---------|---------
qualifierIdentity|(required)|Qualifier identity details|body|    |
partyName|(required)|Party name|path|string|
profileName|(required)|Business profile Name|path|string|
|id|(required)|Business profile id|path|integer|
Response Messages
---



HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204     |No Content |         |       |

  
Example Value
---

```
{
  "Description": "string",
  "Qualifier": "string",
  "Value": "string",
  "Id": 0
}
```
