---
description: "Learn more about: MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI)"
title: MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI)
TOCTitle: MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI)
ms:assetid: 53f35713-c618-463d-abe5-66ff315b706b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560191(v=BTS.80)
ms:contentKeyID: 51528084
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_TrackedMessageInstance2.SaveToFile Method (WMI)

 

This method saves message context and parts into multiple output files.

## Syntax

```C#
  
uint32SaveToFile(string OutputFolderFullPath);  
```

#### Parameters

<table>
<tbody>
<tr class="odd">
<td><strong>OutputFolderFullPath</strong></td>
<td>[in] Describes the full path for the folder that will contain the output files.</td>
</tr>
</tbody>
</table>


## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

