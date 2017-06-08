---
title: "MSBTS_Server.Stop Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b3a74f9-593d-4059-b04e-bd93fefee4a2
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Server.Stop Method (WMI)
Stops all BizTalk Server services on a specific server.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 Stop();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 The execution of this method is valid anytime the specified server is in a running state.  
  
 For more information about the minimum security user rights required to administer a server, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.