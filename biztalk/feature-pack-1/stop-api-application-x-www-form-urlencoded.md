---
title: "Stop API. application x-www-form-urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 20c96992-a2ef-419b-af75-e8baa6826e5b
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Stop API.: application/x-www-form-urlencoded
## Stop API.

  Response Content Type: **application/x-www-form-urlencoded**
  
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
