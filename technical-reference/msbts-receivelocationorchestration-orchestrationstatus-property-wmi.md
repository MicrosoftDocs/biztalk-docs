---
title: MSBTS_ReceiveLocationOrchestration.OrchestrationStatus Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.OrchestrationStatus Property (WMI)
ms:assetid: 6450b2f8-7e1d-4457-a686-9316afa1bc1b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560507(v=BTS.80)
ms:contentKeyID: 51528538
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.OrchestrationStatus Property (WMI)

 

Indicates the status of the orchestration.

*The syntax shown is language neutral.*

## Syntax

``` 
  
uint32 OrchestrationStatus;  
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
<td>Unbound</td>
<td>1</td>
</tr>
<tr class="even">
<td>Bound</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Stopped</td>
<td>3</td>
</tr>
<tr class="even">
<td>Started</td>
<td>4</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

