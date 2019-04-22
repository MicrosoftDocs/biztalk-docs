---
title: Sequence Group Node Properties
TOCTitle: Sequence Group Node Properties
ms:assetid: f9d6a1c2-d85b-416c-b77a-0acc48bc6049
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562045(v=BTS.80)
ms:contentKeyID: 51533552
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Sequence Group Node Properties

 

Use a **Sequence Group** node when all of its child nodes have to occur in instance messages in the exact same order in which they are defined.

When you select a **Sequence Group** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as converting the group definition from local to global.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the allowed number of occurrences of the element group.

Many of the properties associated with **Sequence Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

The following table shows the properties associated with **Sequence Group** nodes that are available in all schemas.

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
<td>Specifies the globally defined group referenced by the selected <strong>Sequence Group</strong> node, or a new name for this group, thereby converting it to a global <strong>Sequence Group</strong> node.</td>
</tr>
<tr class="even">
<td><a href="max-occurs-node-property-of-all-schemas.md">Max Occurs</a></td>
<td>General</td>
<td>Specifies the maximum number of times that the underlying group content of the selected <strong>Sequence Group</strong> node can occur.</td>
</tr>
<tr class="odd">
<td><a href="min-occurs-node-property-of-all-schemas.md">Min Occurs</a></td>
<td>General</td>
<td>Specifies the minimum number of times that the underlying group content of the selected <strong>Sequence Group</strong> node can occur.</td>
</tr>
<tr class="even">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Displays the namespace for the selected <strong>Sequence Group</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Displays the name of the selected <strong>Sequence Group</strong> node, as displayed in the schema tree. This name has one of the following forms:<br />
<br />
- &lt;Sequence&gt; (the default, when the <strong>Group Reference</strong> property has no value).<br />
- &lt;Group:<em>X</em>&gt;, where &quot;<em>X</em>&quot; is the value of the <strong>Group Reference</strong> property.</td>
</tr>
<tr class="even">
<td><a href="order-type-node-property-of-all-schemas.md">Order Type</a></td>
<td>Advanced</td>
<td>Identifies the selected node as a <strong>Sequence Group</strong> node, and allows it to be converted to a <strong>Choice Group</strong> node or, in some circumstances, an <strong>All Group</strong> node.</td>
</tr>
</tbody>
</table>


## See Also

[Choice Group Node Properties](choice-group-node-properties.md)  
[All Group Node Properties](all-group-node-properties.md)  
[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

