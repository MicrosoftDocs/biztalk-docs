---
title: MSBTS_DeploymentService.Export Method (WMI)
TOCTitle: MSBTS_DeploymentService.Export Method (WMI)
ms:assetid: ca5d0029-e1f7-4103-86dc-2d1bf781e055
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547992(v=BTS.80)
ms:contentKeyID: 51531184
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_DeploymentService.Export Method (WMI)

 

Exports the binding file from the target database.

*The syntax shown is language neutral.*

## Syntax

``` 
  
uint32 Export (string Server, string Database, string Assembly, string Name, string Version, string Culture, string PublicKeyToken, string Binding, string Log);  
```

#### Parameters

*Server*  
Name of the SQL server where the BizTalk Management database is located.

*Database*  
Name of the management SQL database.

*Assembly*  
Strong name of the BizTalk assembly (\*.dll) file that specifies the assembly whose binding info will be exported. If this argument is supplied, you do not need to specify input for the *Name*, *Version*, *Culture* and *PublicKeyToken* parameters.

*Name*  
Name of the BizTalk assembly that will specifies the assembly whose binding info will be exported. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.

*Version*  
Version of the BizTalk assembly that specifies the assembly whose binding info will be exported. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.

*Culture*  
Culture of the BizTalk assembly that specifies the assembly whose binding info will be exported. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.

*PublicKeyToken*  
Public key token of the BizTalk assembly that specifies the assembly whose binding info will be exported. If you specify inputs for the *Name*, *Version*, *Culture*, and *PublicKeyToken* parameter, you do not need to specify input for the *Assembly* parameter.

*Binding*  
Pathname to the output BizTalk assembly binding (\*.xml) information file.

*Log*  
Pathname to the output log file.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

