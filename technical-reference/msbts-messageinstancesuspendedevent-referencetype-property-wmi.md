---
title: MSBTS_MessageInstanceSuspendedEvent.ReferenceType Property (WMI)
TOCTitle: MSBTS_MessageInstanceSuspendedEvent.ReferenceType Property (WMI)
ms:assetid: 619ea34b-9c30-4118-b2cd-2c4a6ad7928f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560461(v=BTS.80)
ms:contentKeyID: 51528456
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstanceSuspendedEvent.ReferenceType Property (WMI)

 

Contains information about how this message is referenced by a service.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 ReferenceType;  
```

## Remarks

This property is read-only.

The following table contains the permissible values for this property:

<table>
<thead>
<tr class="header">
<th>Description</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Suspended (resumable)</td>
<td>1</td>
</tr>
<tr class="even">
<td>Suspended (not resumable)</td>
<td>2</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

