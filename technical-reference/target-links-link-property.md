---
description: "Learn more about: Target Links (Link Property)"
title: Target Links (Link Property)
TOCTitle: Target Links (Link Property)
ms:assetid: bca1bf68-bc1a-4b48-83f9-cd8e6e5a1bb9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578372(v=BTS.80)
ms:contentKeyID: 51530870
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Target Links (Link Property)

 

Use the **Target Links** property to determine how the hierarchy below the node that is the target of the link is constructed based on the node that is the source of the link.

## Category

Compiler

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
<td><strong>Flatten Links</strong></td>
<td>Specifies that all source hierarchies are to be flattened to a parent node in the destination schema.</td>
</tr>
<tr class="even">
<td><strong>Match Links Top Down</strong></td>
<td>Specifies that node hierarchies are to be matched from the top of the source and destinations schemas to the bottom of the source and destination schemas.</td>
</tr>
<tr class="odd">
<td><strong>Match Links Bottom Up</strong></td>
<td>Specifies that node hierarchies are to be matched from the bottom of the source and destination schemas to the top of the source and destination schemas.</td>
</tr>
</tbody>
</table>


## Default Value

**Flatten Links**

## Remarks

You can see the effect of this property only when the source and target nodes of the link are at different levels in their respective schemas. This property determines the for-each relationship between the source and target nodes when the data is being copied through this link.

For more information about node hierarchy matching, see [Node-Hierarchy Level Matching](https://msdn.microsoft.com/library/aa560350\(v=bts.80\)).

## See Also

[Link Properties](link-properties.md)

