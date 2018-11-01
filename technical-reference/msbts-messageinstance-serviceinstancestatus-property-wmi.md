---
title: MSBTS_MessageInstance.ServiceInstanceStatus Property (WMI)
TOCTitle: MSBTS_MessageInstance.ServiceInstanceStatus Property (WMI)
ms:assetid: 31964346-5411-4f3c-955e-5535c13c56bc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559482(v=BTS.80)
ms:contentKeyID: 51527137
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.ServiceInstanceStatus Property (WMI)

 

Contains state of the service instance to which this message belongs.

*The syntax shown is language neutral.*

## Syntax

``` 
  
uint32 ServiceInstanceStatus;  
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
<td>Ready to run</td>
<td>1</td>
</tr>
<tr class="even">
<td>Active</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Suspended (resumable)</td>
<td>4</td>
</tr>
<tr class="even">
<td>Dehydrated</td>
<td>8</td>
</tr>
<tr class="odd">
<td>Completed with discarded messages</td>
<td>16</td>
</tr>
<tr class="even">
<td>Suspended (not resumable)</td>
<td>32</td>
</tr>
<tr class="odd">
<td>In breakpoint</td>
<td>64</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

