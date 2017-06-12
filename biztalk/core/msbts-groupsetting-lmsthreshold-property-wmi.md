---
title: "MSBTS_GroupSetting.LMSThreshold Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f12dc3d-b6a9-4c2e-8d94-0d379ddf01fc
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.LMSThreshold Property (WMI)
Gets the threshold size, in bytes, for large message support.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 LMSThreshold;  
```  
  
## Remarks  
 This property is read-write.  
  
 If the in-memory size of a message batch reaches this threshold during processing, the portion of the message batch that has been processed is written to the MessageBox before the remainder of the message batch is processed.  
  
 The default value for this property is 1000000.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.