---
description: "Learn more about: Group Min Occurs (Node Property of All Schemas)"
title: Group Min Occurs (Node Property of All Schemas)
TOCTitle: Group Min Occurs (Node Property of All Schemas)
ms:assetid: 462d442d-2a16-4c57-9f4e-b6330f827acb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559873(v=BTS.80)
ms:contentKeyID: 51527729
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Group Min Occurs (Node Property of All Schemas)

 

Use the **Group Min Occurs** property to specify the minimum number of times the underlying group content of the selected **Record** node can occur in a given scope in an instance message.


> [!NOTE]
> <P>If an ancestor node can occur multiple times, the total occurrences of the selected <STRONG>Record</STRONG> node can be greater than the occurrence range specified by the values of this property and the <A href="group-max-occurs-node-property-of-all-schemas.md">Group Max Occurs</A> property.</P>



## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Advanced

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Edit box value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Positive integer</td>
<td>Any value greater than or equal to one (1), but required to be less than the value set for the <a href="group-max-occurs-node-property-of-all-schemas.md">Group Max Occurs</a> property.</td>
</tr>
<tr class="even">
<td>Zero (0)</td>
<td>Use this value if the underlying group content corresponding to the selected <strong>Record</strong> node need not even occur once in instance messages.</td>
</tr>
<tr class="odd">
<td>No value</td>
<td>Use this property value to restore the behavior to the default value of one (1).</td>
</tr>
</tbody>
</table>


## Default Value

No value, resulting in the default behavior corresponding to a value of one (1).

## XSD Persistence

As the value of the **minOccurs** attribute of the **sequence**, **choice**, or **all** element within the element that corresponds to the selected **Record** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.

Configure this property only for **Record** nodes that have underlying group content.

The value of this property should always be less than or equal to the value of the **Group Max Occurs** property.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

