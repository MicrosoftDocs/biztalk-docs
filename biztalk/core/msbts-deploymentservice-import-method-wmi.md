---
title: "MSBTS_DeploymentService.Import Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a523573-66e8-451c-9f94-4bf0b864cb64
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_DeploymentService.Import Method (WMI)
Imports the binding file into the target database.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 Import (string Server, string Database, string Assembly, boolean Install, string Binding, string Log);  
```  
  
#### Parameters  
 *Server*  
 Name of the SQL server where the BizTalk Management database is located.  
  
 *Database*  
 Name of the management SQL database.  
  
 *Assembly*  
 Pathname to the BizTalk assembly (*.dll) file.  
  
 *Install*  
 **true** to indicate that the assembly should be installed into the global assembly cache; otherwise, **false**.  
  
 *Binding*  
 Pathname to the BizTalk assembly binding information (*.xml) file.  
  
 *Log*  
 Pathname to the output log file.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.