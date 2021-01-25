---
description: "Learn more about: Node Name (Node Property of All Schemas)"
title: Node Name (Node Property of All Schemas)
TOCTitle: Node Name (Node Property of All Schemas)
ms:assetid: 32930e41-ce2a-4161-9696-e5865099ac9a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559500(v=BTS.80)
ms:contentKeyID: 51527168
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Node Name (Node Property of All Schemas)

 

Use the **Node Name** property to display the name of the node as it appears in the schema tree view in BizTalk Editor, and for some types of nodes, to change the name of the node to describe its content.

## Applies to Nodes of Type

[Schema](schema-node-properties.md), [Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md), [Sequence Group](sequence-group-node-properties.md), [Choice Group](choice-group-node-properties.md), [All Group](all-group-node-properties.md), [Attribute Group](attribute-group-node-properties.md), [Any Element](any-element-node-properties.md), [Any Attribute](any-attribute-node-properties.md), [Equivalent](equivalent-node-properties.md), [Equivalent Child](equivalent-child-node-properties.md)

## Category

General

## Allowed Values

Node names must conform to the name requirements of XSD and XML. For those nodes for which the **Node Name** property value can be changed, if you type a node name that does not conform to these requirements, you will be prompted with the following choices:

  - Encode the nonconforming name so that it conforms to XSD/XML requirements.

  - Cancel the naming operation and roll back to the previous name.

For information about the encoding scheme used by BizTalk Editor to encode non-XML characters, see the .NET Framework documentation for the **EncodeLocalName** method of the **System.Xml.XmlConvert** class. BizTalk Editor uses the same encoding scheme.

Two common situations that require encoding are a leading numeral and the space character.

## Default Value

The **Node Name** property has different default values for different types of nodes, as follows:

<table>
<thead>
<tr class="header">
<th>Node type</th>
<th>Node name default values</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Schema</strong></td>
<td>&lt;Schema&gt;</td>
</tr>
<tr class="even">
<td><strong>Record</strong></td>
<td>Record</td>
</tr>
<tr class="odd">
<td><strong>Field Element</strong></td>
<td>Field</td>
</tr>
<tr class="even">
<td><strong>Field Attribute</strong></td>
<td>Field</td>
</tr>
<tr class="odd">
<td><strong>Sequence Group</strong></td>
<td>&lt;Sequence&gt;</td>
</tr>
<tr class="even">
<td><strong>Choice Group</strong></td>
<td>&lt;Choice&gt;</td>
</tr>
<tr class="odd">
<td><strong>All Group</strong></td>
<td>&lt;All&gt;</td>
</tr>
<tr class="even">
<td><strong>Attribute Group</strong></td>
<td>&lt;AttrGroup:attrGroup<em>N</em>&gt;<br />
<br />
where &quot;<em>N</em>&quot; is a monotonically increasing number starting at zero (0)</td>
</tr>
<tr class="odd">
<td><strong>Any Element</strong></td>
<td>&lt;Any&gt;</td>
</tr>
<tr class="even">
<td><strong>Any Attribute</strong></td>
<td>&lt;AnyAttribute&gt;</td>
</tr>
<tr class="odd">
<td><strong>Equivalent</strong></td>
<td>&lt;Equivalent&gt;</td>
</tr>
<tr class="even">
<td><strong>Equivalent Child</strong></td>
<td>The names of the base complex type and set of derived complex types, displayed within angle brackets (&lt;type&gt;), associated with the containing <strong>Equivalent</strong> node.</td>
</tr>
</tbody>
</table>


## XSD Persistence

The **Node Name** property is persisted differently in the XSD for different types of nodes, as follows:

<table>
<thead>
<tr class="header">
<th>Node type</th>
<th>Node name XSD persistence</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Schema</strong></td>
<td>As the <strong>schema</strong> element.</td>
</tr>
<tr class="even">
<td><strong>Record</strong></td>
<td>As the value of the <strong>name</strong> attribute of the corresponding <strong>element</strong> element.</td>
</tr>
<tr class="odd">
<td><strong>Field Element</strong></td>
<td>As the value of the <strong>name</strong> attribute of the corresponding <strong>element</strong> element.</td>
</tr>
<tr class="even">
<td><strong>Field Attribute</strong></td>
<td>As the value of the <strong>name</strong> attribute of the corresponding <strong>attribute</strong> element.</td>
</tr>
<tr class="odd">
<td><strong>Sequence Group</strong></td>
<td>When the <strong>Group Reference</strong> property has no value, as a <strong>sequence</strong> element.<br />
<br />
When the <strong>Group Reference</strong> property has a value, the variable portion of the node name, which follows the leading &quot;Group:&quot; substring, is persisted as the <strong>ref</strong> attribute of the instances of the usage of the sequence group and as the <strong>name</strong> attribute of the global definition of the sequence group.</td>
</tr>
<tr class="even">
<td><strong>Choice Group</strong></td>
<td>When the <strong>Group Reference</strong> property has no value, as a <strong>choice</strong> element.<br />
<br />
When the <strong>Group Reference</strong> property has a value, the variable portion of the node name, which follows the leading &quot;Group:&quot; substring, is persisted as the <strong>ref</strong> attribute of the instances of the usage of the choice group and as the <strong>name</strong> attribute of the global definition of the choice group.</td>
</tr>
<tr class="odd">
<td><strong>All Group</strong></td>
<td>When the <strong>Group Reference</strong> property has no value, as an <strong>all</strong> element.<br />
<br />
When the <strong>Group Reference</strong> property has a value, the variable portion of the node name, which follows the leading &quot;Group:&quot; substring, is persisted as the <strong>ref</strong> attribute of the instances of the usage of the all group and as the <strong>name</strong> attribute of the global definition of the all group.</td>
</tr>
<tr class="even">
<td><strong>Attribute Group</strong></td>
<td>The variable portion of the node name, which follows the leading &quot;AttrGroup:&quot; substring, is persisted as the <strong>ref</strong> attribute of the instances of the usage of the attribute group and as the <strong>name</strong> attribute of the global definition of the attribute group.</td>
</tr>
<tr class="odd">
<td><strong>Any Element</strong></td>
<td>As an <strong>any</strong> element.</td>
</tr>
<tr class="even">
<td><strong>Any Attribute</strong></td>
<td>As an <strong>anyAttribute</strong> element.</td>
</tr>
<tr class="odd">
<td><strong>Equivalent</strong> and <strong>Equivalent Child</strong></td>
<td><strong>Equivalent</strong> and <strong>Equivalent Child</strong> nodes are BizTalk Editor constructs and are not part of the XSD standard. These nodes exist to help you visualize the inheritance that is present among the base types and derived types in the schema.</td>
</tr>
</tbody>
</table>


## Remarks

You can examine this property, and in some cases set this property, in the Visual Studio Properties window when you select a node in BizTalk Editor.

The **Node Name** property behaves differently for different types of nodes, as follows:

<table>
<thead>
<tr class="header">
<th>Node type</th>
<th>Node name property behavior</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Schema</strong></td>
<td>Read-only. It is always set to &quot;&lt;Schema&gt;&quot;.</td>
</tr>
<tr class="even">
<td><strong>Record</strong>, <strong>Field Element</strong>, and <strong>Field Attribute</strong></td>
<td>Read/write. You can rename <strong>Record</strong>, <strong>Field Element</strong>, and <strong>Field Attribute</strong> nodes using the <strong>Node Name</strong> property, or in-place within the schema tree when you first insert them or when you use the <strong>Rename</strong> command on the shortcut menu for the node.<br />
<br />
Sibling <strong>Record</strong> and <strong>Field Element</strong> nodes from the same namespace can only have the same <strong>Node Name</strong> property value if they have the same data type (except when it is a global declaration), and sibling <strong>Field Attribute</strong> nodes from the same namespace can never have the same <strong>Node Name</strong> property value.</td>
</tr>
<tr class="odd">
<td><strong>Sequence Group</strong>, <strong>Choice Group</strong>, and <strong>All Group</strong></td>
<td>Read-only. However, any nonblank value in the corresponding <a href="group-reference-node-property-of-all-schemas.md">Group Reference</a> property contributes to the <strong>Node Name</strong> property value for these element group nodes. For example, if you set the <strong>Group Reference</strong> property to the value &quot;BillingAddress&quot;, the <strong>Node Name</strong> property will become &quot;Group:BillingAddress&quot;.</td>
</tr>
<tr class="even">
<td><strong>Attribute Group</strong></td>
<td>Read-only. However, the value in the corresponding <a href="group-reference-node-property-of-all-schemas.md">Group Reference</a> property, whether the default value or a value you provide, contributes to the <strong>Node Name</strong> property value for <strong>Attribute Group</strong> nodes. For example, if you set the <strong>Group Reference</strong> property to the value &quot;ProductDimensions&quot;, the <strong>Node Name</strong> property will become &quot;AttrGroup:ProductDimensions&quot;.</td>
</tr>
<tr class="odd">
<td>Any Element</td>
<td>Read-only. It is always set to &quot;&lt;Any&gt;&quot;.</td>
</tr>
<tr class="even">
<td>Any Attribute</td>
<td>Read-only. It is always set to &quot;&lt;AnyAttribute&gt;&quot;.</td>
</tr>
<tr class="odd">
<td>Equivalent</td>
<td>Read-only. It is always set to &quot;&lt;Equivalent&gt;&quot;.</td>
</tr>
<tr class="even">
<td>Equivalent Child</td>
<td>Read-only. It is always set to one of the complex type names associated with the parent <strong>Equivalent</strong> node, either the base complex type name or one of the derived complex type names.</td>
</tr>
</tbody>
</table>


## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

