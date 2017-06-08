---
title: "MSBTS_MessageInstance.ReferenceType Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d204971-e7f8-42e4-9e9f-4d33a72fcf0d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstance.ReferenceType Property (WMI)
Contains information about how message is referenced by a service.  
  
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
|Delivered, not consumed|1|  
|Consumed|2|  
|Suspended|4|  
|Abandoned|8|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.