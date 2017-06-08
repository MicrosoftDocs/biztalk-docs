---
title: "MSBTS_ServerHost.Map Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a97cd07c-77bc-41f0-ab23-4328525f5e25
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServerHost.Map Method (WMI)
Maps the server to the MessageBox without installing applications.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 Map();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 You must establish this mapping before an instance of this BizTalk host can be installed on this BizTalk server. You install the instance of the host by calling the **Install** method on the corresponding **MSBTS_HostInstance** instance.  
  
 For samples illustrating the **MSBTS_ServerHost** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.