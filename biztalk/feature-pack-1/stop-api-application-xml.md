---
title: "Stop API. application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: eafd20ee-589a-45ce-99f9-f8da2d662946
caps.latest.revision: 4
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Stop API.: application/xml
## Stop API.

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
<ApplicationStopOptions>
  <UnenlistAllOrchestrations>true</UnenlistAllOrchestrations>
  <UnenlistAllSendPorts>true</UnenlistAllSendPorts>
  <UnenlistAllSendPortGroups>true</UnenlistAllSendPortGroups>
  <DisableAllReceiveLocations>true</DisableAllReceiveLocations>
  <UndeployAllPolicies>true</UndeployAllPolicies>
  <StopReferencedApplications>true</StopReferencedApplications>
  <SuspendRunningInstances>true</SuspendRunningInstances>
</ApplicationStopOptions>
```
