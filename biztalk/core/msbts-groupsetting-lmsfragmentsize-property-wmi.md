---
title: "MSBTS_GroupSetting.LMSFragmentSize Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04099624-c907-4fe5-ae98-17cd09559a8c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.LMSFragmentSize Property (WMI)
Gets or sets the fragment size, in bytes, for large message support.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 LMSFragmentSize;  
```  
  
## Remarks  
 This property is read-write.  
  
 This property is the message size below which messages will be handled in memory. Any message larger than this will be buffered to the file system to reduce memory requirements.  
  
 The default value for this property is 102400.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.