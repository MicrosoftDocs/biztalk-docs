---
title: "MSBTS_Host.Stop Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 835a38b9-fe5d-49b6-abe7-04a565415d9c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.Stop Method (WMI)
Stops all BizTalk Host instances in the BizTalk group for the given BizTalk Host.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 Stop();  
```  
  
## Remarks  
 For more information about the minimum security user rights required to administer a Host, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.