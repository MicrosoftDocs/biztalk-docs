---
title: "MSBTS_ServiceInstanceSuspendedEvent.ServiceStatus Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3f562d8-c254-4244-bc9e-992a223651dd
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstanceSuspendedEvent.ServiceStatus Property (WMI)
Contains the state of the service instance. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
Uint32 ServiceStatus;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Suspended (resumable)|1|  
|Suspended (not resumable)|2|  
|Completed with discarded messages|4|  
  
 Note that the integer values must be used in code and script.  
  
 For sample code illustrating the **MSBTS_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](../core/listening-for-a-suspended-event-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.