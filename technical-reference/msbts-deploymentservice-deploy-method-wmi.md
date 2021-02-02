---
description: "Learn more about: MSBTS_DeploymentService.Deploy Method (WMI)"
title: MSBTS_DeploymentService.Deploy Method (WMI)
TOCTitle: MSBTS_DeploymentService.Deploy Method (WMI)
ms:assetid: 1a7fd9b2-0375-47ef-8c35-7bf37c114968
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559040(v=BTS.80)
ms:contentKeyID: 51526543
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_DeploymentService.Deploy Method (WMI)

 

Deploys the assembly into the target database.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 Deploy (string Server, string Database, string Assembly, boolean Install, string Binding, string Log);  
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
Pathname to the BizTalk assembly binding information (\*.xml) file. This parameter is optional.

*Log*  
Pathname to the output log file.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

