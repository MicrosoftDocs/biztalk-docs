---
title: "MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ceae4612-a215-45b7-a210-be9d39d17be6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI)
Checks if the server can host BizTalk host instances.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 CheckIfCanInstallHostInstances();  
```  
  
## Error Handling  
 S_OK (0) if yes, S_FALSE (1) if no, and FAILED (negative) if otherwise.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.