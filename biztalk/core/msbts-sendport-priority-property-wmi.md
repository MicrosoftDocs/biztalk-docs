---
title: "MSBTS_SendPort.Priority Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f9459d2-d351-4c0e-b215-260c52b28871
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.Priority Property (WMI)
Contains the priority of the send port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```
uint32 Priority;  
```  
  
## Remarks  
 This property is read-write.  
  
 The **Priority** property determines the order in which messages are delivered. 1 is the highest priority, 10 is the lowest priority.  
  
 For example, if messages 1, 2, and 3 are published, and 3 goes to the port A with a priority setting of 1, while 1 and 2 go to port B with a priority setting of 10, then message 3 will be delivered before messages 1 and 2.  
  
 To avoid the prioritization of deliveries, set the **Priority** property to the same value on all ports.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.Priority** property.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.