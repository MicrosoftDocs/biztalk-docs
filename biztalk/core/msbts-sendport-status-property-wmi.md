---
title: "MSBTS_SendPort.Status Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b51ca92-caf5-4e08-bde5-6129b59ed407
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.Status Property (WMI)
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
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.Status** property. For more information about this property, search for the `Status` property.
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.