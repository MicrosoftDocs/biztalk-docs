---
title: "MSBTS_MessageInstanceSuspendedEvent.ReferenceType Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 619ea34b-9c30-4118-b2cd-2c4a6ad7928f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstanceSuspendedEvent.ReferenceType Property (WMI)
Contains information about how this message is referenced by a service.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 ReferenceType;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Suspended (resumable)|1|  
|Suspended (not resumable)|2|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.