---
title: Record Node Properties
TOCTitle: Record Node Properties
ms:assetid: 61d5b2f6-b600-437a-8031-f66d05f131d4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560465(v=BTS.80)
ms:contentKeyID: 51528450
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Record Node Properties

 

When you select a **Record** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as data type derivations.

  - **BizTalk.** This category contains a property that is related to an annotation feature that is specific to Microsoft BizTalk Server.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the data type of the corresponding element or attribute.

  - **Parse.** This category contains a property related to unwrapping envelope content in instance messages.

When you insert a **Record** node, the name of the node as displayed in the schema tree, and which corresponds to its **Node Name** property, is immediately made available for editing within the schema tree. Your choice of a name for this node is particularly important because it defines the name of the corresponding XML element in the instance messages that this schema defines.

Many of the properties associated with **Record** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).


> [!NOTE]
> <P>Some <STRONG>Record</STRONG> node properties are automatically enabled or disabled, or shown or hidden, depending on the values of other node properties.</P>



The following table shows the properties associated with **Record** nodes that are available in all schemas.

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
<td><a href="base-data-type-node-property-of-all-schemas.md">Base Data Type</a></td>
<td>Advanced</td>
<td>Specifies the base data type from which the type for the selected <strong>Record</strong> node is derived.</td>
</tr>
<tr class="even">
<td><a href="block-node-property-of-all-schemas.md">Block</a></td>
<td>General</td>
<td>Prevents or defines allowed derivations of this <strong>Record</strong> node in other schemas.</td>
</tr>
<tr class="odd">
<td><a href="body-xpath-node-property-of-all-schemas.md">Body XPath</a></td>
<td>Parse</td>
<td>Identifies the portion of the schema that defines the body of the message associated with the select root <strong>Record</strong> node in an envelope schema.</td>
</tr>
<tr class="even">
<td><a href="content-type-node-property-of-all-schemas.md">Content Type</a></td>
<td>Advanced</td>
<td>Specifies whether the content of the <strong>Record</strong> node is simple or complex.</td>
</tr>
<tr class="odd">
<td><a href="data-structure-type-node-property-of-all-schemas.md">Data Structure Type</a></td>
<td>General</td>
<td>Specifies a name for the data type of the selected node so that it can be used elsewhere.</td>
</tr>
<tr class="even">
<td><a href="derived-by-node-property-of-all-schemas.md">Derived By</a></td>
<td>Advanced</td>
<td>Specifies how the complex type associated with the selected node is derived from the data type specified by the <strong>Base Data Type</strong> property.</td>
</tr>
<tr class="odd">
<td><a href="final-node-property-of-all-schemas.md">Final</a></td>
<td>General</td>
<td>Specifies derivation restrictions for the data type defined for the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="form-node-property-of-all-schemas.md">Form</a></td>
<td>Advanced</td>
<td>Specifies whether local elements in instance messages must be qualified with a namespace identifier.</td>
</tr>
<tr class="odd">
<td><a href="group-max-occurs-node-property-of-all-schemas.md">Group Max Occurs</a></td>
<td>Advanced</td>
<td>Specifies the maximum number of times the underlying group content of the selected <strong>Record</strong> node can occur.</td>
</tr>
<tr class="even">
<td><a href="group-min-occurs-node-property-of-all-schemas.md">Group Min Occurs</a></td>
<td>Advanced</td>
<td>Specifies the minimum number of times the underlying group content of the selected <strong>Record</strong> node can occur.</td>
</tr>
<tr class="odd">
<td><a href="group-order-type-node-property-of-all-schemas.md">Group Order Type</a></td>
<td>Advanced</td>
<td>Specifies the type of group ordering of child nodes below the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="instance-xpath-node-property-of-all-schemas.md">Instance XPath</a></td>
<td>General</td>
<td>Displays the location within instance messages of the element that corresponds to the selected <strong>Record</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="max-occurs-node-property-of-all-schemas.md">Max Occurs</a></td>
<td>General</td>
<td>Specifies the maximum number of times that the element corresponding to the selected <strong>Record</strong> node can occur.</td>
</tr>
<tr class="even">
<td><a href="min-occurs-node-property-of-all-schemas.md">Min Occurs</a></td>
<td>General</td>
<td>Specifies the minimum number of times that the element corresponding to the selected <strong>Record</strong> node can occur.</td>
</tr>
<tr class="odd">
<td><a href="mixed-node-property-of-all-schemas.md">Mixed</a></td>
<td>Advanced</td>
<td>Specifies that character data or text can appear with subelements in the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Displays the namespace for the selected <strong>Record</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="nillable-node-property-of-all-schemas.md">Nillable</a></td>
<td>Advanced</td>
<td>Specifies whether the <strong>xsi:nil</strong> attribute can be used at run time with the element that corresponds to the selected <strong>Record</strong> node to indicate that it is still valid even if it has no content.</td>
</tr>
<tr class="even">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Specifies the name of the selected <strong>Record</strong> node as it appears in the schema tree view.</td>
</tr>
<tr class="odd">
<td><a href="notes-node-property-of-all-schemas.md">Notes</a></td>
<td>BizTalk</td>
<td>Specifies notes about the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="rootnode-typename-node-property-of-all-schemas.md">RootNode TypeName</a></td>
<td>Reference</td>
<td>Specifies the name that will be used when generating the .NET class name for the selected top-level <strong>Record</strong> root node.</td>
</tr>
</tbody>
</table>


When you select a **Record** node in BizTalk Editor and you have enabled the **Flat File Extension** using the [Schema Editor Extensions](schema-editor-extensions-node-property-of-all-schemas.md) property, you can examine and set additional properties in the Visual Studio Properties window. These properties belong to the **Flat File** category and contain those properties related to parsing flat files in equivalent XML files and serializing XML files back into flat files.

The following table shows the supplemental properties that are available for **Record** nodes when the **Flat File Extension** is enabled.

<table>
<thead>
<tr class="header">
<th>Flat file property name</th>
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="child-delimiter-node-property-of-flat-file-schemas.md">Child Delimiter</a></td>
<td>Flat File</td>
<td>Specifies the string used to delimit fields and subordinate records in the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="child-delimiter-type-node-property-of-flat-file-schemas.md">Child Delimiter Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative child delimiter string will be expressed in the <strong>Child Delimiter</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="odd">
<td><a href="child-order-node-property-of-flat-file-schemas.md">Child Order</a></td>
<td>Flat File</td>
<td>Specifies the relationship between delimiters and the data they delimit.</td>
</tr>
<tr class="even">
<td><a href="escape-character-node-property-of-flat-file-schemas.md">Escape Character</a></td>
<td>Flat File</td>
<td>Specifies a character to be used as the escape character for the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.<br />
<br />
An escape character causes the following character to be interpreted as simple data, and to not have the special meaning otherwise associated with it.</td>
</tr>
<tr class="odd">
<td><a href="escape-character-type-node-property-of-flat-file-schemas.md">Escape Character Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative escape character will be expressed in the <strong>Escape Character</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="even">
<td><a href="preserve-delimiter-for-empty-data-node-property-of-flat-file-schemas.md">Preserve Delimiter For Empty Data</a></td>
<td>Flat File</td>
<td>Specifies whether the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node will have delimiters for empty fields and subordinate records.</td>
</tr>
<tr class="odd">
<td><a href="repeating-delimiter-node-property-of-flat-file-schemas.md">Repeating Delimiter</a></td>
<td>Flat File</td>
<td>Specifies the string used to delimit repeating fields and subordinate records in the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="repeating-delimiter-type-node-property-of-flat-file-schemas.md">Repeating Delimiter Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative repeating delimiter string will be expressed in the <strong>Repeating Delimiter</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="odd">
<td><a href="structure-node-property-of-flat-file-schemas.md">Structure</a></td>
<td>Flat File</td>
<td>Specifies whether the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node is positional or delimited.</td>
</tr>
<tr class="even">
<td><a href="suppress-trailing-delimiters-node-property-of-flat-file-schemas.md">Suppress Trailing Delimiters</a></td>
<td>Flat File</td>
<td>Specifies whether trailing delimiters will be suppressed when output instance messages are serialized.</td>
</tr>
<tr class="odd">
<td><a href="tag-identifier-node-property-of-flat-file-schemas.md">Tag Identifier</a></td>
<td>Flat File</td>
<td>Specifies an identifying tag for the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.</td>
</tr>
<tr class="even">
<td><a href="tag-offset-node-property-of-flat-file-schemas.md">Tag Offset</a></td>
<td>Flat File</td>
<td>Specifies the starting offset of the tag, relative to the previous sibling or delimiter, for the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.</td>
</tr>
</tbody>
</table>


## See Also

[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

