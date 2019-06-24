---
title: Choice Group Node Properties
TOCTitle: Choice Group Node Properties
ms:assetid: a21c8808-d5d8-49da-bdf5-26893f4d5092
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577806(v=BTS.80)
ms:contentKeyID: 51530180
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Choice Group Node Properties

 

Use a **Choice Group** node when exactly one of its child nodes can occur in instance messages.

When you select a **Choice Group** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as converting the group definition from local to global.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the allowed number of occurrences of the element group.

Many of the properties associated with **Choice Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

The following table shows the properties associated with **Choice Group** nodes that are available in all schemas.

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
<td>Specifies the globally defined group referenced by the selected <strong>Choice Group</strong> node, or a new name for this group, thereby converting it to a global <strong>Choice Group</strong> node.</td>
</tr>
<tr class="even">
<td><a href="max-occurs-node-property-of-all-schemas.md">Max Occurs</a></td>
<td>General</td>
<td>Specifies the maximum number of times that to the underlying group content of the selected <strong>Choice Group</strong> node can occur.</td>
</tr>
<tr class="odd">
<td><a href="min-occurs-node-property-of-all-schemas.md">Min Occurs</a></td>
<td>General</td>
<td>Specifies the minimum number of times that the underlying group content of the selected <strong>Choice Group</strong> node can occur.</td>
</tr>
<tr class="even">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Displays the namespace for the selected <strong>Choice Group</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Displays the name of the selected <strong>Choice Group</strong> node, as displayed in the schema tree. This name has one of the following forms:<br />
<br />
- &lt;Choice&gt; (the default, when the <strong>Group Reference</strong> property has no value).<br />
- &lt;Group:<em>X</em>&gt;, where &quot;<em>X</em>&quot; is the value of the <strong>Group Reference</strong> property.</td>
</tr>
<tr class="even">
<td><a href="order-type-node-property-of-all-schemas.md">Order Type</a></td>
<td>Advanced</td>
<td>Identifies the selected node as a <strong>Choice Group</strong> node, and allows it to be converted to a <strong>Sequence Group</strong> node or, in some circumstances, an <strong>All Group</strong> node.</td>
</tr>
</tbody>
</table>


## See Also

[Sequence Group Node Properties](sequence-group-node-properties.md)  
[All Group Node Properties](all-group-node-properties.md)  
[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

