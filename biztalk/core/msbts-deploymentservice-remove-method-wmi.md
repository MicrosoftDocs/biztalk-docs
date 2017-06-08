---
title: "MSBTS_DeploymentService.Remove Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9bccd96-e5b7-41ff-868e-95429bccd452
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_DeploymentService.Remove Method (WMI)
Removes the assembly from the target database.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 Remove (string Server, string Database, string Assembly, string Name, string Version, string Culture, string PublicKeyToken, boolean UnInstall, string Log);  
```  
  
#### Parameters  
 *Server*  
 Name of the SQL server where the BizTalk Management database is located.  
  
 *Database*  
 Name of the management SQL database.  
  
 *Assembly*  
 Pathname to the BizTalk assembly (\*.dll) file. If this argument is supplied, you do not need to specify input for the *Name*, *Version*, *Culture* and *PublicKeyToken* parameters.  
  
 *Name*  
 Name of the BizTalk assembly. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.  
  
 *Version*  
 Version of the BizTalk assembly. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.  
  
 *Culture*  
 Culture of the BizTalk assembly. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.  
  
 *PublicKeyToken*  
 Public key token of the BizTalk assembly. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.  
  
 *UnInstall*  
 This parameter is ignored. Whether **true** or **false**, the assembly will not be uninstalled from the global assembly cache.  
  
> [!NOTE]
>  To properly uninstall an assembly from the GAC, refer to [How to Uninstall an Assembly from the GAC](../Topic/How%20to%20Uninstall%20an%20Assembly%20from%20the%20GAC.md).  
  
 *Log*  
 Pathname to the output log file.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.