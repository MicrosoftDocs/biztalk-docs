---
title: "MSBTS_GroupSetting.UnRegisterLocalServer Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f20282a5-d710-4dbf-b01e-f9ed5d08c967
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.UnRegisterLocalServer Method (WMI)
Deletes the Windows NT registry information set up by the **RegisterLocalServer** method.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 UnRegisterLocalServer();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 This method should only be invoked internally by BizTalk Server  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.