---
title: MSBTS_MessageInstance.ServiceClass Property (WMI)
TOCTitle: MSBTS_MessageInstance.ServiceClass Property (WMI)
ms:assetid: 4137d3a0-2380-43de-8734-c3383a505d34
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559782(v=BTS.80)
ms:contentKeyID: 51527546
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.ServiceClass Property (WMI)

 

Contains the name of the service class that corresponds to the message instance.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 ServiceClass;  
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
<td>Orchestration</td>
<td>1</td>
</tr>
<tr class="even">
<td>Tracking</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Messaging</td>
<td>4</td>
</tr>
<tr class="even">
<td>Other</td>
<td>16</td>
</tr>
<tr class="odd">
<td>Isolated adapter</td>
<td>32</td>
</tr>
<tr class="even">
<td>Routing failure report</td>
<td>64</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

