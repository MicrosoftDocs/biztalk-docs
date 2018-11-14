---
title: Max Occurs (Node Property of All Schemas)
TOCTitle: Max Occurs (Node Property of All Schemas)
ms:assetid: 0ecf0ff2-26c3-4420-951c-a09f763b7c3d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547387(v=BTS.80)
ms:contentKeyID: 51526245
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Max Occurs (Node Property of All Schemas)

 

Use the **Max Occurs** property to configure the maximum number of times that the element or elements corresponding to the selected node can occur in a given scope in an instance message.


> [!NOTE]
> <P>If an ancestor node can occur multiple times, the total occurrences of the selected node can be greater than the occurrence range specified by the values of the <A href="min-occurs-node-property-of-all-schemas.md">Min Occurs</A> property and this property.</P>



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
<td>Non-negative integer</td>
<td>Any value greater than one (1) will enable the corresponding element(s) in an instance message to occur up to that many times. To prohibit multiple occurrences, set the value of this property to one (1) or leave it blank. To prevent all occurrences, set the value of this property to zero (0).<br />
<br />
The maximum value for Max Occurs is 4095. If you need a value greater than this, use &quot;unbounded&quot; as described below.</td>
</tr>
<tr class="even">
<td>&quot;unbounded&quot;<br />
<br />
&quot;*&quot;</td>
<td>Use this value if you do not know how many loops you might have in an instance message and you do not want to lose any data. An asterisk (*) is a BizTalk Editor abbreviation for the literal string value &quot;unbounded&quot;.</td>
</tr>
<tr class="odd">
<td>No value</td>
<td>Use this property value to restore the behavior to the default value of one (1).</td>
</tr>
</tbody>
</table>


## Default Value

No value, indicating the default behavior associated with the value one (1).

## XSD Persistence

As the value of the **maxOccurs** attribute of the element that corresponds to the selected node.


> [!NOTE]
> <P>The literal string "unbounded", and not an asterisk (*), is persisted in the XSD.</P>



## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a node of an appropriate type in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

When you set this property to any value other than **1**, BizTalk Mapper compiles the selected node as a looping record. If you configure this property with a value of **1**, BizTalk Mapper will not compile the selected node as a looping record.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

