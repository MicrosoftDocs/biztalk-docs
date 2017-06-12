---
title: "Stop API. application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 1e2fe43b-3667-446b-9405-482fdc3a453b
caps.latest.revision: 4
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Stop API.: application/json
## Stop API.

  Response Content Type: **application/json**
  
  Parameters
  ---
  
  

Parameter |Value |Description |Parameter Type|Data Type
---------|---------|---------|---------|---------
applicationName|(required)   |The application name.|path |string |
applicationStopOptions|(required)|The application stop options. |body | |


Response Messages
---

HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204   |No Content    |         |         |

Example Value
---

```
{
  "UnenlistAllOrchestrations": true,
  "UnenlistAllSendPorts": true,
  "UnenlistAllSendPortGroups": true,
  "DisableAllReceiveLocations": true,
  "UndeployAllPolicies": true,
  "StopReferencedApplications": true,
  "SuspendRunningInstances": true
}
```
