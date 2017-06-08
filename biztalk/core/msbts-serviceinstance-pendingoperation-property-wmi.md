---
title: "MSBTS_ServiceInstance.PendingOperation Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9acee351-b855-49c0-9adc-d2eac20d3ef6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstance.PendingOperation Property (WMI)
Contains the type of a pending operations (if any) for this service instance. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 PendingOperation;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|No operation|1|  
|Suspend|2|  
|Terminate|4|  
|Resume|8|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.