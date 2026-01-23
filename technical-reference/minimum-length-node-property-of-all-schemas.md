---
description: "Learn more about: Minimum Length (Node Property of All Schemas)"
title: Minimum Length (Node Property of All Schemas)
TOCTitle: Minimum Length (Node Property of All Schemas)
ms:assetid: fe25af72-30c4-4f17-afd8-597b269f4935
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562144(v=BTS.80)
ms:contentKeyID: 51533785
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Minimum Length (Node Property of All Schemas)

 

Use the **Minimum Length** property to specify the minimum length for any instance message data corresponding to the selected **Field Element** or **Field Attribute** node.

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
<td>Non-negative integer</td>
<td>Specifies the minimum length for data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td>No value</td>
<td>Use this value to clear the property, resulting in no minimum length restrictions for the corresponding data in an instance message.</td>
</tr>
</tbody>
</table>


## Default Value

No value.

## XSD Persistence

As the value of the **minLength** element and its **value** attribute.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived Type** property to **Restriction**.

This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.

This property applies to unordered base data types, such as **xs:string**, as well as to list-based restriction derivations, specifying the minimum number of space-separated list items that can occur in the corresponding element(s) or attribute(s) in instance messages.

You can either specify a value for the **Maximum Length** and/or **Minimum Length** properties, or for the **Length** property, but not both.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

