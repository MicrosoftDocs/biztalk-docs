---
title: "MSBTS_ServiceInstance.ServiceClass Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 579015b7-4b61-4b84-a240-fd5544848abd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstance.ServiceClass Property (WMI)
Contains the name of the service class that corresponds to the message instance. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint ServiceClass;  
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
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.