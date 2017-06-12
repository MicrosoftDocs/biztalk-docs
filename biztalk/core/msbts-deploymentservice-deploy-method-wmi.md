---
title: "MSBTS_DeploymentService.Deploy Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a7fd9b2-0375-47ef-8c35-7bf37c114968
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_DeploymentService.Deploy Method (WMI)
Deploys the assembly into the target database.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 Deploy (string Server, string Database, string Assembly, boolean Install, string Binding, string Log);  
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
 Pathname to the BizTalk assembly binding information (*.xml) file. This parameter is optional.  
  
 *Log*  
 Pathname to the output log file.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.