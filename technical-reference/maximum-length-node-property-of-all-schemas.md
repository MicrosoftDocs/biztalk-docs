---
description: "Learn more about: Maximum Length (Node Property of All Schemas)"
title: Maximum Length (Node Property of All Schemas)
TOCTitle: Maximum Length (Node Property of All Schemas)
ms:assetid: 44fb4f75-fdd9-463d-bba2-6a1e3836981e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559850(v=BTS.80)
ms:contentKeyID: 51527698
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Maximum Length (Node Property of All Schemas)

 

Use the **Maximum Length** property to specify the maximum length for any instance message data corresponding to the selected **Field Element** or **Field Attribute** node.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Restricted

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Positive integer</td>
<td>Specifies the maximum length for data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td>No value</td>
<td>Use this value to clear the property, resulting in no maximum length restrictions for the corresponding data in an instance message. This is the default value.</td>
</tr>
</tbody>
</table>


## Default Value

No value.

## XSD Persistence

As the value of the **maxLength** element and its **value** attribute.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.

This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.

This property applies to unordered base data types, such as **xs:string**, as well as to list-based restriction derivations, specifying the maximum number of space-separated list items that can occur in the corresponding element(s) or attribute(s) in instance messages.

You can either specify a value for the **Maximum Length** and/or **Minimum Length** properties, or for the **Length** property, but not both.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

