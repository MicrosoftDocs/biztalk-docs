---
title: "MSBTS_Host.IsDefault Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f13c1666-0263-42b7-8b0e-770b246b44f4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.IsDefault Property (WMI)
Indicates whether the BizTalk Host represented by this WMI instance is the default BizTalk Host in the BizTalk group.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
boolean IsDefault;  
```  
  
## Remarks  
 This property is read-write.  
  
 By default, BizTalk Server uses this host to host the orchestration during the orchestration enlistment process. The default host is by default the first host created. After you run the Configuration Wizard, the first In-process host is the default host for the BizTalk Group. You can explicitly choose a different host as the default for your BizTalk Server environment. You can identify the default host in the BizTalk Server Administration console because it has a checkmark symbol.  
  
> [!NOTE]
>  You cannot delete a default host. You must first select a new default host.  
  
> [!NOTE]
>  When there is only one host in a BizTalk group, it cannot be deleted, as this is the default host.  
  
> [!NOTE]
>  Isolated hosts cannot be marked as the default host.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.