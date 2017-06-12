---
title: "Update business identity application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c7a62254-55f7-4cbc-ab4b-6241451b113f
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update business identity: application/x-www-form-urlencoded
## Create business identity

  Response Content Type: **application/x-www-form-urlencoded**

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