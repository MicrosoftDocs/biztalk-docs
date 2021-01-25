---
description: "Learn more about: MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI)"
title: MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI)
TOCTitle: MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI)
ms:assetid: f8098051-f686-4aa9-8f5e-fd7f803fa814
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562005(v=BTS.80)
ms:contentKeyID: 51533520
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance2.SourceDBName Property (WMI)

 

This parameter contains the name of the SQL database where the tracked message is stored.

## Syntax

```C#
  
stringSourceDBName;  
```

## Returned value

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

The default value for this parameter is "".

The maximum length for this parameter is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

