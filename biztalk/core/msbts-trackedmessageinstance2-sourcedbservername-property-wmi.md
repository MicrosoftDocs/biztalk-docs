---
title: "MSBTS_TrackedMessageInstance2.SourceDBServerName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b7825fa-d098-452a-b8f9-588f90d99348
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance2.SourceDBServerName Property (WMI)
Name of the SQL server where the tracked message is stored (either MessageBox or Archived DB). ")]  
  
## Syntax  
  
```  
  
stringSourceDBServerName;  
```  
  
## Return Value  
 Possible values for this parameter are:  
  
|Value|  
|-----------|  
|MessageBox|  
|Archived DB|  
  
## Remarks  
 The syntax shown is language neutral.  
  
 This parameter is read only.  
  
 The maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.