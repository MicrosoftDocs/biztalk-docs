---
title: "Start API. text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: aa4f3963-c932-43b5-a33d-023084a5fc8a
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Start API.: text/json
## Start API.

  Response Content Type: **text/json**
  
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
