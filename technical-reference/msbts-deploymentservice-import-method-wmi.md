---
title: MSBTS_DeploymentService.Import Method (WMI)
TOCTitle: MSBTS_DeploymentService.Import Method (WMI)
ms:assetid: 4a523573-66e8-451c-9f94-4bf0b864cb64
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559978(v=BTS.80)
ms:contentKeyID: 51527831
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_DeploymentService.Import Method (WMI)

 

Imports the binding file into the target database.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 Import (string Server, string Database, string Assembly, boolean Install, string Binding, string Log);  
```

#### Parameters

*Server*  
Name of the SQL server where the BizTalk Management database is located.

*Database*  
Name of the management SQL database.

*Assembly*  
Pathname to the BizTalk assembly (\*.dll) file.

*Install*  
**true** to indicate that the assembly should be installed into the global assembly cache; otherwise, **false**.

*Binding*  
Pathname to the BizTalk assembly binding information (\*.xml) file.

*Log*  
Pathname to the output log file.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

