---
title: MSBTS_SendPortGroup.Status Property (WMI)
TOCTitle: MSBTS_SendPortGroup.Status Property (WMI)
ms:assetid: 9929a112-a6b8-4399-8d32-5a45b14ba4ad
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577490(v=BTS.80)
ms:contentKeyID: 51529873
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup.Status Property (WMI)

 

Displays the current status of the port.

*The syntax shown is language neutral.*

## Syntax

```C#
uint32 Status;  
```

## Return Value

The following table contains the permissible values for this property:

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Bound</strong></td>
<td>1</td>
<td>Default state</td>
</tr>
<tr class="even">
<td><strong>Started</strong></td>
<td>3</td>
<td>Indicates the send port or send port group is started, and subscriptions are activated.</td>
</tr>
<tr class="odd">
<td><strong>Stopped</strong></td>
<td>2</td>
<td>Indicates the send port or send port group is enlisted, and subscriptions are created but they are deactivated.</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Remarks

This property is read-only.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPortGroup.Status** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

