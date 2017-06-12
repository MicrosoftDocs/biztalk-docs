---
title: "Start API. application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 2ea94721-6c36-4164-b912-b10dbed1c889
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Start API.: application/json
## Start API.

  Response Content Type: **application/json**
  
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
