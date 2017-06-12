---
title: "MSBTS_SendPort.SendPipeline Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c39d383-22f5-4519-b0f9-72dcc65ee75c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.SendPipeline Property (WMI)
Contains the name of the send pipeline for the port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
string SendPipeline;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The maximum length for this property is 256 characters.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.SendPipeline** property. 
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.