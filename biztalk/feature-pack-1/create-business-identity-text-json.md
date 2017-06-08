---
title: "Create business identity text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: a6643efb-0fee-450b-83d9-6812bdb8459a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create business identity: text/json
## Create business identity

  Response Content Type: **text/json**

Parameters
---


Parameter|Value  |Description |Parameter Type|Data Type  
---------|---------|---------|---------|---------
qualifierIdentity|(required)|Qualifier identity details|body|         |
partyName|(required)|Party name|path|string|
profileName|(required)|Profile name|path|string|

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
