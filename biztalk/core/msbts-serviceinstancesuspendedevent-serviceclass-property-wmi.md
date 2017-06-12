---
title: "MSBTS_ServiceInstanceSuspendedEvent.ServiceClass Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3608e63f-fc11-4f2b-8338-37e1dd772711
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstanceSuspendedEvent.ServiceClass Property (WMI)
Contains the class of the service instance to which this message belongs. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 ServiceClass;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Orchestration|1|  
|Tracking|2|  
|Messaging|4|  
|MSMQT|8|  
|Other|16|  
|Isolated adapter|32|  
|Routing failure report|64|  
  
 Note that the integer values must be used in code and script.  
  
 For sample code illustrating the **MSBTS_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](../core/listening-for-a-suspended-event-using-wmi.md).