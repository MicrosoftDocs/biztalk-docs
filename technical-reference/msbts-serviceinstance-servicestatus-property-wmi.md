---
title: MSBTS_ServiceInstance.ServiceStatus Property (WMI)
TOCTitle: MSBTS_ServiceInstance.ServiceStatus Property (WMI)
ms:assetid: 82ec2502-2df3-401c-a86e-9f41967d5076
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561123(v=BTS.80)
ms:contentKeyID: 51529336
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstance.ServiceStatus Property (WMI)

 

Contains the state of the service instance to which this message belongs. The syntax shown is language neutral.

## Syntax

```C#
  
uint32 ServiceStatus;  
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

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

