---
title: "MSBTS_SendPortGroup.Status Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9929a112-a6b8-4399-8d32-5a45b14ba4ad
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPortGroup.Status Property (WMI)
Displays the current status of the port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
uint32 Status;  
```  
  
## Return Value  
 The following table contains the permissible values for this property:  
  
|Member name|Value|Description|  
|-----------------|-----------|-----------------|  
|**Bound**|1|Default state|  
|**Started**|3|Indicates the send port or send port group is started, and subscriptions are activated.|  
|**Stopped**|2|Indicates the send port or send port group is enlisted, and subscriptions are created but they are deactivated.|  
  
 Note that the integer values must be used in code and script.  
  
## Remarks  
 This property is read-only.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPortGroup.Status** property.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.