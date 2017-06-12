---
title: "Update an Application text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: d86287b0-a226-474b-93d8-78720a89c35b
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update an Application: text/json
## Update an Application

  Response Content Type: **text/json**
  
  Parameters
  ---
  
  

Parameter |Value |Description |Parameter Type|Data Type
---------|---------|---------|---------|---------
applicationName|(required)   |Name of Application to be updated|path |string |
application|(required)    |Details of Application to be updated|body  |   |


Response Messages
---

HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204   |No Content    |         |         |

Example Value
---

```
{
  "Name": "string",
  "Description": "string",
  "IsDefaultApplication": true,
  "IsSystem": true,
  "Status": "string",
  "IsConfigured": true,
  "ApplicationReferences": [
    "string"
  ],
  "ApplicationBackReferences": [
    "string"
  ]
}
```

