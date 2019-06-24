---
title: Source Links (Link Property)
TOCTitle: Source Links (Link Property)
ms:assetid: 9dc062d9-5de5-4e8f-a493-98ff4976c6b9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577591(v=BTS.80)
ms:contentKeyID: 51529984
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Source Links (Link Property)

 

Use the **Source Links** property to specify the source of the data that will be copied to the destination of the link.

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
<td><strong>Copy Name</strong></td>
<td>Specifies that the name of the node that is the source of the link is to be copied to the destination of the link.</td>
</tr>
<tr class="even">
<td><strong>Copy Text Value</strong></td>
<td>Specifies that the value of the node that is the source of the link is to be copied to the destination of the link.</td>
</tr>
<tr class="odd">
<td><strong>Copy Text and Subcontent Value</strong></td>
<td>The value corresponding to the record node, and the value of all its child nodes, and their child nodes, in the source schema (element data and attribute values) are combined as the value of the linked node in the destination schema. For example, &lt;Node&gt;Hello&lt;Name&gt;John&lt;/Name&gt;Smith&lt;/Node&gt; would result in &quot;Hello John Smith&quot;.</td>
</tr>
</tbody>
</table>


## Default Value

**Copy Text Value**

## See Also

[Link Properties](link-properties.md)

