---
title: "MSBTS_Server.Start Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3618084a-ccb4-4534-bcbf-e135c385bcdf
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Server.Start Method (WMI)
Starts all BizTalk Server services on a specific server.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 Start();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 The execution of this method is valid anytime the server is in a stopped state.  
  
 For more information about the minimum security user rights required to administer a server, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.