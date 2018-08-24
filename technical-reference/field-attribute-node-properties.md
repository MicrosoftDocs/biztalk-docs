---
title: Field Attribute Node Properties
TOCTitle: Field Attribute Node Properties
ms:assetid: aea31ecf-ef0b-47a8-844f-2175b6ea1c90
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578079(v=BTS.80)
ms:contentKeyID: 51530529
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Field Attribute Node Properties

 

When you select a **Field Attribute** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. These properties are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as data type derivations.

  - **BizTalk.** This category contains properties that are related to usability and annotation features that are specific to Microsoft BizTalk Server.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the data type of the corresponding element or attribute.

  - **Restricted.** This category contains properties that correspond to XSD concepts related to type derivations through restriction.

When you insert a **Field Attribute** node, the name of the node as displayed in the schema tree, and which corresponds to its **Node Name** property, is immediately made available for editing within the schema tree. Your choice of a name for this node is important because it defines the name of the corresponding XML attribute in the instance messages that this schema defines.

Many of the properties associated with **Field Attribute** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs. For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).


> [!NOTE]
> <P>Some <STRONG>Field Attribute</STRONG> node properties are automatically enabled or disabled, or shown or hidden, depending on the values of other node properties.</P>



The following table shows the properties associated with **Field Attribute** nodes that are available in all schemas.

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
<td>Specifies the base data type from which the type for the selected <strong>Field Attribute</strong> node is derived.</td>
</tr>
<tr class="even">
<td><a href="codelist-node-property-of-all-schemas.md">CodeList</a></td>
<td>BizTalk</td>
<td>Specifies the reference number for the code list to use with the selected <strong>Field Attribute</strong> node and provides access to the <strong>CodeList</strong> dialog box.</td>
</tr>
<tr class="odd">
<td><a href="data-type-node-property-of-all-schemas.md">Data Type</a></td>
<td>General</td>
<td>Specifies the name of an existing data type for the selected <strong>Field Attribute</strong> node or specifies a name for this data type that can be used elsewhere.</td>
</tr>
<tr class="even">
<td><a href="default-value-node-property-of-all-schemas.md">Default Value</a></td>
<td>General</td>
<td>Specifies the default value for the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="derived-by-node-property-of-all-schemas.md">Derived By</a></td>
<td>Advanced</td>
<td>Specifies how the underlying simple type of this <strong>Field Attribute</strong> node is derived from its base type (by Restriction, List, or Union).</td>
</tr>
<tr class="even">
<td><a href="enumeration-node-property-of-all-schemas.md">Enumeration</a></td>
<td>Restricted</td>
<td>Limits any data in an instance message corresponding to the selected <strong>Field Attribute</strong> node to a specific set of values.</td>
</tr>
<tr class="odd">
<td><a href="field-type-node-property-of-all-schemas.md">Field Type</a></td>
<td>General</td>
<td>Identifies the selected <strong>Field Attribute</strong> node as a <strong>Field Attribute</strong> node as opposed to a <strong>Field Element</strong> node.</td>
</tr>
<tr class="even">
<td><a href="final-node-property-of-all-schemas.md">Final</a></td>
<td>Advanced</td>
<td>Specifies derivation restrictions for the data type defined for the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="fixed-node-property-of-all-schemas.md">Fixed</a></td>
<td>Advanced</td>
<td>Specifies a fixed value for the attribute(s) in an instance message that corresponds to the selected <strong>Field Attribute</strong> node, if the data is present.</td>
</tr>
<tr class="even">
<td><a href="form-node-property-of-all-schemas.md">Form</a></td>
<td>Advanced</td>
<td>Specifies whether local attributes in instance messages must be qualified with a namespace identifier.</td>
</tr>
<tr class="odd">
<td><a href="instance-xpath-node-property-of-all-schemas.md">Instance XPath</a></td>
<td>General</td>
<td>Displays the location within instance messages of the attribute that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="item-type-node-property-of-all-schemas.md">Item Type</a></td>
<td>Advanced</td>
<td>Specifies the data type of the corresponding attribute(s) in instance messages when the <strong>Derived By</strong> property is set to <strong>List</strong>.</td>
</tr>
<tr class="odd">
<td><a href="length-node-property-of-all-schemas.md">Length</a></td>
<td>Restricted</td>
<td>Specifies the fixed length of the data corresponding to the selected <strong>Field Attribute</strong> node in instance messages.</td>
</tr>
<tr class="even">
<td><a href="maxfacet-type-node-property-of-all-schemas.md">MaxFacet Type</a></td>
<td>Restricted</td>
<td>Specifies whether the upper bound of the ordered value for any data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node, as specified by the <strong>MaxFacet Value</strong> property, is inclusive or exclusive.</td>
</tr>
<tr class="odd">
<td><a href="maxfacet-value-node-property-of-all-schemas.md">MaxFacet Value</a></td>
<td>Restricted</td>
<td>Specifies the maximum value (inclusive or exclusive, as specified by the <strong>MaxFacet Type</strong> property) for any data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="maximum-length-node-property-of-all-schemas.md">Maximum Length</a></td>
<td>Restricted</td>
<td>Specifies the maximum length for data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="member-types-node-property-of-all-schemas.md">Member Types</a></td>
<td>Advanced</td>
<td>Specifies the list of valid data types for the corresponding attribute(s) in instance messages when the <strong>Derived By</strong> property is set to <strong>Union</strong>.</td>
</tr>
<tr class="even">
<td><a href="minfacet-type-node-property-of-all-schemas.md">MinFacet Type</a></td>
<td>Restricted</td>
<td>Specifies whether the lower bound of the ordered value for any data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node, as specified by the <strong>MaxFacet Value</strong> property, is inclusive or exclusive.</td>
</tr>
<tr class="odd">
<td><a href="minfacet-value-node-property-of-all-schemas.md">MinFacet Value</a></td>
<td>Restricted</td>
<td>Specifies the minimum value (inclusive or exclusive, as specified by the <strong>MinFacet Type</strong> property) for any data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="minimum-length-node-property-of-all-schemas.md">Minimum Length</a></td>
<td>Restricted</td>
<td>Specifies the minimum length for data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td>General</td>
<td>Displays the namespace for the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Specifies the name of the selected <strong>Field Attribute</strong> node as it appears in the schema tree view.</td>
</tr>
<tr class="odd">
<td><a href="notes-node-property-of-all-schemas.md">Notes</a></td>
<td>BizTalk</td>
<td>Specifies notes about the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="pattern-node-property-of-all-schemas.md">Pattern</a></td>
<td>Restricted</td>
<td>Limits any data in an instance message corresponding to the selected <strong>Field Attribute</strong> node to a specific pattern, as specified by one or more regular expressions.</td>
</tr>
<tr class="odd">
<td><a href="use-requirement-node-property-of-all-schemas.md">Use Requirement</a></td>
<td>General</td>
<td>Specifies whether the attribute that corresponds to the selected <strong>Field Attribute</strong> node is required in an instance message.</td>
</tr>
</tbody>
</table>


When you select a **Field Attribute** node in BizTalk Editor and you have enabled the **Flat File Extension** using the [Schema Editor Extensions](schema-editor-extensions-node-property-of-all-schemas.md) property, you can examine and set additional properties in the Visual Studio Properties window. These properties are divided into the existing category **Reference** and the new category **Flat File**, the latter of which contains those properties related to parsing flat files in equivalent XML files and serializing XML files back into flat files.

The following table shows the supplemental properties that are available for **Field Attribute** nodes when the **Flat File Extension** is enabled.

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
<td><a href="custom-date-time-format-node-property-of-flat-file-schemas.md">Custom Date/Time Format</a></td>
<td>Flat File</td>
<td>Specifies the format for your custom date/time type when the selected <strong>Field Element</strong> node is set to one of the following XSD data types or a simple type derived from one of them: <strong>Note:</strong> xs:date, xs:dateTime, xs:time, xs:gYearMonth, xs:gYear, xs:gMonthDay, xs:gDay, or xs:gMonth</td>
</tr>
<tr class="even">
<td><a href="justification-node-property-of-flat-file-schemas.md">Justification</a></td>
<td>Flat File</td>
<td>Specifies the left or right justification of the contents of the field(s) that correspond to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="minimum-length-with-pad-character-node-property-of-flat-file-schemas.md">Minimum Length with Pad Character</a></td>
<td>Flat File</td>
<td>Specifies how a serializer pads the data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="pad-character-node-property-of-flat-file-schemas.md">Pad Character</a></td>
<td>Flat File</td>
<td>Specifies the pad character to be used for data in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="pad-character-type-node-property-of-flat-file-schemas.md">Pad Character Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative pad character will be expressed in the <strong>Pad Character</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="even">
<td><a href="positional-length-node-property-of-flat-file-schemas.md">Positional Length</a></td>
<td>Reference</td>
<td>Specifies the length, from the previous sibling or delimiter, of the field in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="odd">
<td><a href="positional-offset-node-property-of-flat-file-schemas.md">Positional Offset</a></td>
<td>Reference</td>
<td>Specifies the starting offset, relative to the previous sibling or delimiter, of the field in instance messages that corresponds to the selected <strong>Field Attribute</strong> node.</td>
</tr>
<tr class="even">
<td><a href="wrap-character-node-property-of-flat-file-schemas.md">Wrap Character</a></td>
<td>Flat File</td>
<td>Specifies a character to be used as the wrap character for the field(s) in an instance message that corresponds to the selected <strong>Field Attribute</strong> node.<br />
<br />
Wrap characters cause the characters that occur between them to be interpreted as simple data, and to not have the special meaning otherwise associated with it.</td>
</tr>
<tr class="odd">
<td><a href="wrap-character-type-node-property-of-flat-file-schemas.md">Wrap Character Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative wrap character will be expressed in the <strong>Wrap Character</strong> property and in the underlying XSD representation.</td>
</tr>
</tbody>
</table>


## See Also

[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

