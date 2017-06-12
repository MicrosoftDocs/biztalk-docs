---
title: "Start API. application x-www-form-urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e4f4a0e9-aa56-417d-ae6c-52d858de6d1a
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Start API.: application/x-www-form-urlencoded
## Start API.

  Response Content Type: **application/x-www-form-urlencoded**
  
  Parameters
  ---
  
  

Parameter |Value |Description |Parameter Type|Data Type
---------|---------|---------|---------|---------
applicationName|(required)   |The application name.|path |string |
applicationStartOptions|(required)|The application start options. |body | |


Response Messages
---

HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204   |No Content    |         |         |

Example Value
---

```
{
  "StartAllOrchestrations": true,
  "StartAllSendPorts": true,
  "StartAllSendPortGroups": true,
  "EnableAllReceiveLocations": true,
  "DeployAllPolicies": true,
  "StartReferencedApplications": true
}
```
