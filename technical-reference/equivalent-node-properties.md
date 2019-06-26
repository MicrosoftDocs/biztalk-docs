---
title: Equivalent Node Properties
TOCTitle: Equivalent Node Properties
ms:assetid: b77dc843-fce6-4397-a133-eabd1b446256
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578276(v=BTS.80)
ms:contentKeyID: 51530757
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Equivalent Node Properties

 

**Equivalent** nodes are created automatically by BizTalk Editor to show how derived complex types can be used instead of the base complex type from which they are derived wherever the base complex type is called for in the schema. This yields the same type of polymorphism that is common in many object-oriented programming languages.

At the location in an instance message where the base complex type is called for by the schema, the structure of the XML can validly conform to that base complex type or to any of the derived complex types, all of which are displayed as child nodes of the **Equivalent** node in the schema.

When you select an **Equivalent** node in BizTalk Editor, you can examine its read-only properties in the Visual Studio Properties window.

The following table shows the properties associated with **Equivalent** node.

<table>
<thead>
<tr class="header">
<th>Property name</th>
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="base-type-node-property-of-all-schemas.md">Base Type</a></td>
<td>General</td>
<td>Shows the base complex type upon which the named derivations are based.</td>
</tr>
<tr class="even">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Shows that this node is an <strong>Equivalent</strong> node by displaying the value &quot;&lt;Equivalent&gt;&quot;.</td>
</tr>
</tbody>
</table>


## See Also

[Equivalent Child Node Properties](equivalent-child-node-properties.md)  
[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

