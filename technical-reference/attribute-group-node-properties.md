---
title: Attribute Group Node Properties
TOCTitle: Attribute Group Node Properties
ms:assetid: f7384d51-9a79-4e69-b436-67bb74db8aac
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561988(v=BTS.80)
ms:contentKeyID: 51533474
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Attribute Group Node Properties

 

When you select an **Attribute Group** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as changing the name by which the group definition is referenced.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as its namespace and name.

**Sequence Group**, **Choice Group**, and **All Group** nodes, collectively known as element group nodes, can be either local or global, depending on whether you give their **Group Reference** property a value. Unlike these element group nodes, **Attribute Group** nodes are always global and are given a default value for their **Group Reference** property of the form "\<AttrGroup:attrGroup*N*\>", where "N" is a monotonically increasing number, starting at zero (0).

Further, **Attribute Group** nodes have no structure beyond the set of attributes that they group together for collective use, whereas element group nodes can have very deep structures.

Many of the properties associated with **Attribute Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).

The following table shows the properties associated with **Attribute Group** nodes that are available in all schemas.

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
<td><a href="group-reference-node-property-of-all-schemas.md">Group Reference</a></td>
<td>Advanced</td>
<td>Specifies the globally defined group referenced by the selected <strong>Attribute Group</strong> node.</td>
</tr>
<tr class="even">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Displays the namespace for the selected <strong>Attribute Group</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Displays the name of the selected <strong>Attribute Group</strong> node, as displayed in the schema tree. This name is of the form:<br />
<br />
- &lt;AttrGroup:<em>X</em>&gt;, where &quot;<em>X</em>&quot; is the value of the <strong>Group Reference</strong> property.</td>
</tr>
</tbody>
</table>


## See Also

[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

