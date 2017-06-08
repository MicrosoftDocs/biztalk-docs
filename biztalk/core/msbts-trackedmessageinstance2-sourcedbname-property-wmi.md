---
title: "MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8098051-f686-4aa9-8f5e-fd7f803fa814
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI)
This parameter contains the name of the SQL database where the tracked message is stored.  
  
## Syntax  
  
```  
  
stringSourceDBName;  
```  
  
## Returned value  
  
|Value|  
|-----------|  
|MessageBox|  
|Archived DB|  
  
## Remarks  
 The syntax shown is language neutral.  
  
 This parameter is read only.  
  
 The default value for this parameter is "".  
  
 The maximum length for this parameter is 123 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.