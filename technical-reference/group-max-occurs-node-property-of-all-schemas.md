---
description: "Learn more about: Group Max Occurs (Node Property of All Schemas)"
title: Group Max Occurs (Node Property of All Schemas)
TOCTitle: Group Max Occurs (Node Property of All Schemas)
ms:assetid: 17318b5b-29b9-42d7-88af-b2a742cf3f60
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558767(v=BTS.80)
ms:contentKeyID: 51526458
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Group Max Occurs (Node Property of All Schemas)

 

Use the **Group Max Occurs** property to specify the maximum number of times the underlying group content of the selected **Record** node can occur in a given scope in an instance message.


> [!NOTE]
> <P>If an ancestor node can occur multiple times, the total occurrences of the selected <STRONG>Record</STRONG> node can be greater than the occurrence range specified by the values of the <A href="group-min-occurs-node-property-of-all-schemas.md">Group Min Occurs</A> property and this property.</P>



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
<td>Non-negative integer</td>
<td>Any value greater than one (1) will enable the underlying content that corresponds to the selected <strong>Record</strong> node to occur multiple times in an instance message. If you do not want the underlying content to occur more than once, set the value of this property to one (1), or leave it blank. To prevent all occurrences, set the value of this property to zero (0).</td>
</tr>
<tr class="even">
<td>&quot;unbounded&quot;<br />
<br />
&quot;*&quot;</td>
<td>Use this value if you do not know how many loops you might have in an instance message and you do not want to lose any data. An asterisk (&quot;*&quot;) is a valid abbreviation for the literal string value &quot;unbounded&quot;.</td>
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

As the value of the **maxOccurs** attribute of the **sequence**, **choice**, or **all** element within the element that corresponds to the selected **Record** node.


> [!NOTE]
> <P>The literal string "unbounded", and not an asterisk (*), is persisted in the XSD.</P>



## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.

Configure this property only for **Record** nodes that have underlying group content.

The value of this property should always be greater than or equal to the value of the **Group Min Occurs** property.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

