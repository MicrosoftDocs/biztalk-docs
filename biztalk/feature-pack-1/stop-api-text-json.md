---
title: "Stop API. text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c6ab5d74-0642-40e9-b2db-c449d3bb1614
caps.latest.revision: 4
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Stop API.: text/json
## Stop API.

  Response Content Type: **text/json**
  
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
