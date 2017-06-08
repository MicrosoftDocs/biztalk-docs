---
title: "MSBTS_GroupSetting.RegisterLocalServer Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a26237-b546-45b3-b297-6758ecc4ea6a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.RegisterLocalServer Method (WMI)
Sets up the Windows NT registry of the local computer to point to this BizTalk group.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 RegisterLocalServer();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 This method should only be invoked internally by BizTalk Server.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.