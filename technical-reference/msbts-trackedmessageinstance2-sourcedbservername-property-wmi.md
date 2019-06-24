---
title: MSBTS_TrackedMessageInstance2.SourceDBServerName Property (WMI)
TOCTitle: MSBTS_TrackedMessageInstance2.SourceDBServerName Property (WMI)
ms:assetid: 1b7825fa-d098-452a-b8f9-588f90d99348
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559063(v=BTS.80)
ms:contentKeyID: 51526607
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance2.SourceDBServerName Property (WMI)

 

Name of the SQL server where the tracked message is stored (either MessageBox or Archived DB). ")\]

## Syntax

```C#
  
stringSourceDBServerName;  
```

## Return Value

Possible values for this parameter are:

<table>
<thead>
<tr class="header">
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>MessageBox</td>
</tr>
<tr class="even">
<td>Archived DB</td>
</tr>
</tbody>
</table>


## Remarks

The syntax shown is language neutral.

This parameter is read only.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

