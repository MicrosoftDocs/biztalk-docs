---
description: "Learn more about: Form (Node Property of All Schemas)"
title: Form (Node Property of All Schemas)
TOCTitle: Form (Node Property of All Schemas)
ms:assetid: f111b9cd-8343-457f-9c90-1dc96b2463eb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561862(v=BTS.80)
ms:contentKeyID: 51533324
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Form (Node Property of All Schemas)

 

Use the **Form** property to define whether local elements and attributes in instance messages must be qualified with a namespace identifier.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Advanced

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
<td><strong>(Default)</strong></td>
<td>Removes the <strong>form</strong> attribute, if present, specifying the default behavior, which corresponds to the <strong>Unqualified</strong> setting.</td>
</tr>
<tr class="even">
<td><strong>Qualified</strong></td>
<td>Sets the <strong>form</strong> attribute to &quot;qualified&quot;, specifying that locally declared elements must be qualified by a namespace identifier in instance messages.</td>
</tr>
<tr class="odd">
<td><strong>Unqualified</strong></td>
<td>Sets the <strong>form</strong> attribute to &quot;unqualified&quot;, specifying that locally declared elements need not be qualified by a namespace identifier in instance messages.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, specifying the default behavior corresponding to the **Unqualified** setting.

## XSD Persistence

As the **form** (="qualified" or "unqualified") attribute of the **element** or **attribute** element that corresponds to the selected **Record**, **Field Element**, or **Field Attribute**, respectively.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record**, **Field Element**, or **Field Attribute** node in BizTalk Editor.

This property provides the ability to specify the requirements for namespace qualification on a node-by-node basis.

For **Record** and **Field Element** nodes, the **Form** property overrides the setting of the [Element FormDefault](element-formdefault-node-property-of-all-schemas.md) property of the **Schema** node.

For **Field Attribute** nodes, the **Form** property overrides the setting of the [Attribute FormDefault](attribute-formdefault-node-property-of-all-schemas.md) property of the **Schema** node.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

