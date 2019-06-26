---
title: Copy Processing Instructions (PIs) (Grid Property)
TOCTitle: Copy Processing Instructions (PIs) (Grid Property)
ms:assetid: dadc1164-16c5-466c-9419-2395405d54aa
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561403(v=BTS.80)
ms:contentKeyID: 51531686
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Copy Processing Instructions (PIs) (Grid Property)

 

Use the **Copy Processing Instructions (PIs)** property to specify whether any processing instructions found in the input instance message should be copied to the output instance message during transformation.

## Category

Custom Header

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>True</strong></td>
<td>Specifies that processing instructions should be copied from the input instance message to the output instance message.</td>
</tr>
<tr class="even">
<td><strong>False</strong></td>
<td>Specifies that processing instructions should not be copied from the input instance message to the output instance message.</td>
</tr>
</tbody>
</table>


## Default Value

**False**

## Remarks

A processing instruction is an item in an XML file that is used to provide instructions to an application that processes the XML file. Within an XML file, processing instructions are delimited by "\<?" and "?\>".


> [!NOTE]
> <P>The Copy Processing Instructions property copies instructions only from one message to another, single message. Processing instructions cannot be copied from or to all of the parts in multi-part mappings (one-to-many or many-to-one).</P>




> [!NOTE]
> <P>You cannot undo or redo the <STRONG>Copy Processing Instructions (PIs)</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

