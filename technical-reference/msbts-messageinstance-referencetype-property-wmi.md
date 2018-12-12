---
title: MSBTS_MessageInstance.ReferenceType Property (WMI)
TOCTitle: MSBTS_MessageInstance.ReferenceType Property (WMI)
ms:assetid: 7d204971-e7f8-42e4-9e9f-4d33a72fcf0d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560993(v=BTS.80)
ms:contentKeyID: 51529177
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.ReferenceType Property (WMI)

 

Contains information about how message is referenced by a service.

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
<td>Delivered, not consumed</td>
<td>1</td>
</tr>
<tr class="even">
<td>Consumed</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Suspended</td>
<td>4</td>
</tr>
<tr class="even">
<td>Abandoned</td>
<td>8</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

