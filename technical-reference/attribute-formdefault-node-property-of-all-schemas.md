---
description: "Learn more about: Attribute FormDefault (Node Property of All Schemas)"
title: Attribute FormDefault (Node Property of All Schemas)
TOCTitle: Attribute FormDefault (Node Property of All Schemas)
ms:assetid: 46cfd564-b2d0-4d9a-ba11-0ccef79cf81f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559892(v=BTS.80)
ms:contentKeyID: 51527758
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Attribute FormDefault (Node Property of All Schemas)

 

Use the **Attribute FormDefault** property to define whether locally declared attributes must be qualified by using a namespace identifier throughout instance messages.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

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
<td>Removes the <strong>attributeFormDefault</strong> attribute, if present, specifying the default behavior corresponding to the &quot;Unqualified&quot; setting.</td>
</tr>
<tr class="even">
<td><strong>Qualified</strong></td>
<td>Sets the <strong>attributeFormDefault</strong> attribute to &quot;qualified&quot;, specifying that locally declared attributes must be qualified by a namespace identifier throughout instance messages.</td>
</tr>
<tr class="odd">
<td><strong>Unqualified</strong></td>
<td>Sets the <strong>attributeFormDefault</strong> attribute to &quot;unqualified&quot;, specifying that locally declared attributes need not be qualified by a namespace identifier throughout instance messages.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, specifying default behavior corresponding to the "Unqualified" setting.

## XSD Persistence

As the value of the **attributeFormDefault** attribute of the **schema** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

You can override the global setting established by this property by setting the [Form](form-node-property-of-all-schemas.md) property for individual **Field Attribute** nodes.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[Form (Node Property of All Schemas)](form-node-property-of-all-schemas.md)

