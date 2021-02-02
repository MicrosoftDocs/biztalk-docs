---
description: "Learn more about: Element FormDefault (Node Property of All Schemas)"
title: Element FormDefault (Node Property of All Schemas)
TOCTitle: Element FormDefault (Node Property of All Schemas)
ms:assetid: 80e0ff7d-38cb-49dc-9044-1a2547752f63
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561070(v=BTS.80)
ms:contentKeyID: 51529272
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Element FormDefault (Node Property of All Schemas)

 

Use the **Element FormDefault** property to define whether locally declared elements must be qualified by using a namespace identifier throughout instance messages.

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
<td>Removes the <strong>elementFormDefault</strong> attribute, if present, specifying the default behavior, which corresponds to the &quot;Unqualified&quot; setting.</td>
</tr>
<tr class="even">
<td><strong>Qualified</strong></td>
<td>Sets the <strong>elementFormDefault</strong> attribute to &quot;qualified&quot;, specifying that locally declared elements must be qualified by a namespace identifier throughout instance messages.</td>
</tr>
<tr class="odd">
<td><strong>Unqualified</strong></td>
<td>Sets the <strong>elementFormDefault</strong> attribute to &quot;unqualified&quot;, specifying that locally declared elements need not be qualified by a namespace identifier throughout instance messages.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, specifying the default behavior, which corresponds to the "Unqualified" setting.

## XSD Persistence

As the value of the **elementFormDefault** attribute of the **schema** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

You can override the global setting established by this property by setting the [Form](form-node-property-of-all-schemas.md) property for individual **Record** and **Field Element** nodes.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[Form (Node Property of All Schemas)](form-node-property-of-all-schemas.md)

