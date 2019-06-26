---
title: MSBTS_MessageInstance.SaveToFile Method (WMI)
TOCTitle: MSBTS_MessageInstance.SaveToFile Method (WMI)
ms:assetid: 7758e76b-a0e6-4830-9974-b82365f03265
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560882(v=BTS.80)
ms:contentKeyID: 51529034
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.SaveToFile Method (WMI)

 

Enables an administrator to save message context and parts into multiple output files.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 SaveToFile(string OutputFolderFullPath);  
```

#### Parameters

*OutputFolderFullPath*  
The full name of the output path in which to save the message context and parts.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

