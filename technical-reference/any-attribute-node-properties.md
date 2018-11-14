---
title: Any Attribute Node Properties
TOCTitle: Any Attribute Node Properties
ms:assetid: e23a71b6-68f8-42e1-9415-3d6b71658592
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561552(v=BTS.80)
ms:contentKeyID: 51532946
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Any Attribute Node Properties

 

This node represents the XSD \<anyAttribute\> construct.

When you select an **Any Attribute** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are all in the **General** category.

As you develop a schema, you may insert **Any Attribute** nodes to represent a portion of an instance message for which the attributes cannot be anticipated.

Unlike many other types of nodes, which you can and should rename, the **Any Attribute** node has the fixed node name "\<AnyAttribute\>", which you cannot change.

Many of the properties associated with **Any Attribute** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).


> [!NOTE]
> <P>You can use the <STRONG>Any Attribute</STRONG> node with Extensible Markup Language (XML) schemas only. The <STRONG>Standard</STRONG> property of the <STRONG>Schema</STRONG> node must have a value of <STRONG>XML</STRONG> or <STRONG>Default</STRONG> for this node type to be allowed without generating a compilation error.</P>



The following table shows the properties associated with **Any Attribute** nodes that are available in all schemas that represent XML instance messages.

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
<td><a href="instance-xpath-node-property-of-all-schemas.md">Instance XPath</a></td>
<td>General</td>
<td>Displays the location within instance messages of the attribute(s) that corresponds to the selected <strong>Any Attribute</strong> node. <strong>Note:</strong> The XPath value displayed for this property is not technically valid because the actual node name is not known in advance.</td>
</tr>
<tr class="even">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Specifies the namespace for the selected <strong>Any Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Indicates that this node is an <strong>Any Attribute</strong> node by displaying the value &quot;&lt;AnyAttribute&gt;&quot;.</td>
</tr>
<tr class="even">
<td><a href="process-contents-node-property-of-all-schemas.md">Process Contents</a></td>
<td>General</td>
<td>Specifies the level of validation for data in instance messages that corresponds to the selected <strong>Any Attribute</strong> node.</td>
</tr>
</tbody>
</table>


## See Also

[Any Element Node Properties](any-element-node-properties.md)  
[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

