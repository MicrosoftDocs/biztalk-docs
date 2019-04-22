---
title: Min Occurs (Node Property of All Schemas)
TOCTitle: Min Occurs (Node Property of All Schemas)
ms:assetid: f9676bf6-3a90-4d7f-822e-47c28cf31717
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562037(v=BTS.80)
ms:contentKeyID: 51533567
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Min Occurs (Node Property of All Schemas)

 

Use the **Min Occurs** property to specify the minimum number of times that the element(s) corresponding to the selected node can occur in a given scope in an instance message.


> [!NOTE]
> <P>If an ancestor node can occur multiple times, the total occurrences of the selected node can be greater than the occurrence range specified by the values of this property and the <A href="max-occurs-node-property-of-all-schemas.md">Max Occurs</A> property.</P>



## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Sequence Group](sequence-group-node-properties.md), [Choice Group](choice-group-node-properties.md), [All Group](all-group-node-properties.md), [Any Element](any-element-node-properties.md)

## Category

General

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
<td>Any value greater than or equal to one (1) will require the corresponding element(s) in an instance message to occur at least that many times. The value of this property must be less than the value set for the <a href="max-occurs-node-property-of-all-schemas.md">Max Occurs</a> property of the same ndoe.</td>
</tr>
<tr class="even">
<td>Zero (0)</td>
<td>Use this value if the element(s) corresponding to the selected node need not even occur once in instance messages.</td>
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

As the value of the **minOccurs** attribute of the element that corresponds to the selected node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select node of an appropriate type, including root **Record** nodes, in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

Any value set for this property must be less than or equal to the value specified for the **Max Occurs** property.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

