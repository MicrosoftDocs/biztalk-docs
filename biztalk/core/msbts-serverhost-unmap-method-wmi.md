---
title: "MSBTS_ServerHost.Unmap Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0566f22-ce16-4205-a491-b7f9efe247ae
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServerHost.Unmap Method (WMI)
Unmaps the server from the MessageBox.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 Unmap();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 After you have successfully uninstalled this instance of the BizTalk host from this BizTalk server, this method remove the mapping for the BizTalk server from the BizTalk host.  
  
 For samples illustrating the **MSBTS_ServerHost** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.