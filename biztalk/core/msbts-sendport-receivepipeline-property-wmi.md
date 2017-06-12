---
title: "MSBTS_SendPort.ReceivePipeline Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46be81e8-ed56-4d56-aeb2-49ff4464c1bd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.ReceivePipeline Property (WMI)
Contains the name of the receive pipeline for the port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
string ReceivePipeline;  
```  
  
## Remarks  
 This property is required for instance creation for solicit-response (two-way) send ports. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The maximum length for this property is 256 characters.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.ReceivePipeline** property.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.