---
description: "Learn more about: Final (Node Property of All Schemas)"
title: Final (Node Property of All Schemas)
TOCTitle: Final (Node Property of All Schemas)
ms:assetid: dfbfd5b8-a9dc-404d-aa9a-6fad259bd319
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561500(v=BTS.80)
ms:contentKeyID: 51532862
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Final (Node Property of All Schemas)

 

Use the **Final** property to specify settings that will restrict different types of derivations from the data type defined for the selected **Record**, **Field Element**, or **Field Attribute** node.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

General Category for Record

Advanced Category for Element and Attribute

## Allowed Values

The following table shows the values that can be set for this property when a **Record** node is selected in BizTalk Editor.

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>final</strong> attribute, if present, specifying that there are no restrictions regarding how the data type defined for the selected <strong>Record</strong> node can be derived.</td>
</tr>
<tr class="even">
<td><strong>All</strong></td>
<td>Sets the <strong>final</strong> attribute to &quot;#all&quot;, preventing all derivations from the data type defined for the selected <strong>Record</strong> node.</td>
</tr>
<tr class="odd">
<td><strong>Restriction</strong></td>
<td>Adds &quot;restriction&quot; to the value of the <strong>final</strong> attribute, preventing derivations by restriction from the data type defined for the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><strong>Extension</strong></td>
<td>Adds &quot;extension&quot; to the value of the <strong>final</strong> attribute, preventing derivations by extension from the data type defined for the selected <strong>Record</strong> node.</td>
</tr>
</tbody>
</table>


The following table shows the values that can be set for this property when a **Field Element** or **Field Attribute** node is selected in BizTalk Editor.

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>final</strong> attribute, if present, specifying that there are no restrictions regarding how the data type defined for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node can be derived.</td>
</tr>
<tr class="even">
<td><strong>All</strong></td>
<td>Sets the <strong>final</strong> attribute to &quot;#all&quot;, preventing all derivations from the data type defined for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><strong>Restriction</strong></td>
<td>Adds &quot;restriction&quot; to the value of the <strong>final</strong> attribute, preventing derivations by restriction from the data type defined for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><strong>List</strong></td>
<td>Adds &quot;list&quot; to the value of the <strong>final</strong> attribute, preventing new data types from being derived using lists from the data type defined for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><strong>Union</strong></td>
<td>Adds &quot;union&quot; to the value of the <strong>final</strong> attribute, preventing new data types from being derived using unions from the data type defined for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, specifying that there are no restrictions regarding how the data type defined for the selected **Record**, **Field Element**,or **Field Attribute** node can be inherited.

## XSD Persistence

For **Record** nodes, as a **final** attribute of the **complexType** element that corresponds to the selected **Record** node, set to either "\#all" or some combination of the strings "extension" and "restriction".

For **Field Element** and **Field Attribute** nodes, as a **final** attribute of the **simpleType** element that corresponds to the selected **Field Element** and **Field Attribute** node, set to either "\#all" or some combination of the strings "list", "restriction", and "union".

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** (including a root **Record** node), **Field Element**, or **Field Attribute** node in BizTalk Editor.

When you configure this property, you can prevent all derivations, or restrict, extend, or set the default derivation from a base type.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

For **Record** nodes, the values **Restriction** and **Extension** can be set in combination with each other by selecting their corresponding check boxes in the **Final** property drop-down list. The corresponding values of the **final** attribute are space-separated.

For **Field Element** and **Field Attribute** nodes, the values **Restriction**, **List**, and **Union** can be set in combination with each other by selecting their corresponding check boxes in the **Final** property drop-down list. The corresponding values of the **final** attribute are space-separated.

For more information about different types of derivations, see [Type Reuse and Derivations](https://msdn.microsoft.com/library/aa559208\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[FinalDefault (Node Property of All Schemas)](finaldefault-node-property-of-all-schemas.md)

