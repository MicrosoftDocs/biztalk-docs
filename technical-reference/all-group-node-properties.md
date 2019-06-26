---
title: All Group Node Properties
TOCTitle: All Group Node Properties
ms:assetid: b030e1b7-2bc5-4204-a541-0dd2cca0d202
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578115(v=BTS.80)
ms:contentKeyID: 51530572
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# All Group Node Properties

 

Use an **All Group** node when all of its child nodes may appear once or not at all, and in any order, in instance messages.

When you select an **All Group** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as converting the group definition from local to global.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the allowed number of occurrences of the element group.

Many of the properties associated with **All Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

The following table shows the properties associated with **All Group** nodes that are available in all schemas.

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
<td>Specifies the globally defined group referenced by the selected <strong>All Group</strong> node, or a new name for this group, thereby converting it to a global <strong>All Group</strong> node.</td>
</tr>
<tr class="even">
<td><a href="max-occurs-node-property-of-all-schemas.md">Max Occurs</a></td>
<td>General</td>
<td>Specifies the maximum number of times that to the underlying group content of the selected <strong>All Group</strong> node can occur.</td>
</tr>
<tr class="odd">
<td><a href="min-occurs-node-property-of-all-schemas.md">Min Occurs</a></td>
<td>General</td>
<td>Specifies the minimum number of times that the underlying group content of the selected <strong>All Group</strong> node can occur.</td>
</tr>
<tr class="even">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Displays the namespace for the selected <strong>All Group</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Displays the name of the selected <strong>All Group</strong> node, as displayed in the schema tree. This name has one of the following forms:<br />
<br />
- &lt;All&gt; (the default, when the <strong>Group Reference</strong> property has no value).<br />
- &lt;Group:<em>X</em>&gt;, where &quot;<em>X</em>&quot; is the value of the <strong>Group Reference</strong> property.</td>
</tr>
<tr class="even">
<td><a href="order-type-node-property-of-all-schemas.md">Order Type</a></td>
<td>Advanced</td>
<td>Identifies the selected node as an <strong>All Group</strong> node, and allows it to be converted to a <strong>Sequence Group</strong> or <strong>Choice Group</strong> node.</td>
</tr>
</tbody>
</table>


## See Also

[Sequence Group Node Properties](sequence-group-node-properties.md)  
[Choice Group Node Properties](choice-group-node-properties.md)  
[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

