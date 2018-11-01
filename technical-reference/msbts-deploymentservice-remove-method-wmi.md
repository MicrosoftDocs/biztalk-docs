---
title: MSBTS_DeploymentService.Remove Method (WMI)
TOCTitle: MSBTS_DeploymentService.Remove Method (WMI)
ms:assetid: d9bccd96-e5b7-41ff-868e-95429bccd452
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578710(v=BTS.80)
ms:contentKeyID: 51531662
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_DeploymentService.Remove Method (WMI)

 

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
> <P>To properly uninstall an assembly from the GAC, refer to <A href="https://msdn.microsoft.com/en-us/library/aa559881(v=bts.80)">How to Uninstall an Assembly from the GAC</A>.</P>



*Log*  
Pathname to the output log file.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

