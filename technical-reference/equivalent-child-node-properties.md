---
title: Equivalent Child Node Properties
TOCTitle: Equivalent Child Node Properties
ms:assetid: b0c313db-da7e-4436-bcca-61be09785bd5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578130(v=BTS.80)
ms:contentKeyID: 51530592
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Equivalent Child Node Properties

 

Nodes that are child node of an **Equivalent** node are created automatically by BizTalk Editor to show the set of derived complex types and the base complex type from which they are derived. The XML structures specified by any of these types can occur wherever the base complex type is called for in the schema. This yields the same type of polymorphism that is common in many object-oriented programming languages.

At the location in an instance message where the base complex type is called for by the schema, the structure of the XML can validly conform to that base complex type or to any of the derived complex types, all of which are displayed as child nodes of the **Equivalent** node in the schema.

In corresponding instance messages, you can use any of the types shown under the **Equivalent** node by specifying the data type explicitly:

``` 
<RecordName   
            xmlns:xsi="http://www.w3c.org/2001/XMLSchema-instance">  
  
```

When you select a node that is the child of an **Equivalent** node in BizTalk Editor, you can examine its read-only properties in the Visual Studio Properties window.

The following table shows the properties associated with nodes that are child nodes of **Equivalent** nodes.

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
<td><a href="derivation-type-node-property-of-all-schemas.md">Derivation Type</a></td>
<td>General</td>
<td>Shows the base complex type or one of the derived complex types.</td>
</tr>
<tr class="even">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Shows the name of the base or derived complex type within angle brackets (&lt;type&gt;).</td>
</tr>
</tbody>
</table>


## See Also

[Equivalent Node Properties](equivalent-node-properties.md)  
[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

