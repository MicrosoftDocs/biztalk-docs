---
title: "Start API. application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: eaa9aff7-4de1-4630-8ac4-1790a3695a20
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Start API.: application/xml
## Start API.

  Response Content Type: **application/xml**
  
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
\<?xml version="1.0"?>
<BTApplicationStartOptions>
  <StartAllOrchestrations>true</StartAllOrchestrations>
  <StartAllSendPorts>true</StartAllSendPorts>
  <StartAllSendPortGroups>true</StartAllSendPortGroups>
  <EnableAllReceiveLocations>true</EnableAllReceiveLocations>
  <DeployAllPolicies>true</DeployAllPolicies>
  <StartReferencedApplications>true</StartReferencedApplications>
</BTApplicationStartOptions>
```
