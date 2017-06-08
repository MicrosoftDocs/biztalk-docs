---
title: "MSBTS_MessageInstanceSuspendedEvent.ServiceClass Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8464a83d-d1cc-4f14-9c75-900166ebe2bd
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstanceSuspendedEvent.ServiceClass Property (WMI)
Contains the class of the service instance to which this message belongs.  
  
 *The syntax shown is language neutral.*  
  
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
|Other|16|  
|Isolated adapter|32|  
|Routing failure report|64|  
  
 Note that the integer values must be used in code and script.