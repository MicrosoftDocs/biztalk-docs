---
title: "MSBTS_ReceivePort.SendPipeline Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6442bab4-6d49-4285-a2d0-d45fcbdea3fe
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceivePort.SendPipeline Property (WMI)
Contains the name of the send pipeline for the port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```
string SendPipeline;  
```  
  
## Remarks  
 The maximum length for this property is 256 characters.  
  
 This property is required for instance creation for a request-response (two-way) receive port. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort.SendPipeline** property.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.