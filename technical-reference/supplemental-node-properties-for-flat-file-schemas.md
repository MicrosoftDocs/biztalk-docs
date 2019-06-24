---
title: Supplemental Node Properties for Flat File Schemas
TOCTitle: Supplemental Node Properties for Flat File Schemas
ms:assetid: 02149f63-8031-4c09-bf64-220739e6e7b2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa546762(v=BTS.80)
ms:contentKeyID: 51525891
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Supplemental Node Properties for Flat File Schemas

 

This section provides an alphabetically organized set of reference topics for the supplemental node properties that are available within schemas when you have enabled the **Flat File Extension** using the [Schema Editor Extensions](schema-editor-extensions-node-property-of-all-schemas.md) property.

Because some of these node properties can apply to more than one type of node, the following table and each node property reference topic contains a column or section, respectively, that indicates the node types to which the property applies.

The following table shows the nodes properties that are available in schemas designed for use with flat file instance messages.

<table>
<thead>
<tr class="header">
<th>Flat file property name</th>
<th>Applies to node type(s)</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="case-node-property-of-flat-file-schemas.md">Case</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether data in instance messages should be converted to all uppercase, converted to all lowercase, or left as is.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="child-delimiter-node-property-of-flat-file-schemas.md">Child Delimiter</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the string used to delimit fields and subordinate records in the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="child-delimiter-type-node-property-of-flat-file-schemas.md">Child Delimiter Type</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies how an alternative child delimiter string will be expressed in the <strong>Child Delimiter</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="child-order-node-property-of-flat-file-schemas.md">Child Order</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the relationship between delimiters and the data they delimit.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="code-page-node-property-of-flat-file-schemas.md">Code Page</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the code page to use with an instance message.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="count-positions-in-bytes-node-property-of-flat-file-schemas.md">Count Positions In Bytes</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether the positions will be counted in bytes.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="custom-date-time-format-node-property-of-flat-file-schemas.md">Custom Date/Time Format</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the format for your custom date/time type when the selected <strong>Field Element</strong> node is set to one of the following XSD data types or a simple type derived from one of them:<br />
<br />
xs:date, xs:dateTime, xs:time, xs:gYearMonth, xs:gYear, xs:gMonthDay, xs:gDay, or xs:gMonth<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="default-child-delimiter-node-property-of-flat-file-schemas.md">Default Child Delimiter</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the default string used to delimit fields and subordinate records in the record(s) in an instance message that corresponds to the selected node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="default-child-delimiter-type-node-property-of-flat-file-schemas.md">Default Child Delimiter Type</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies how an alternative default child delimiter string will be expressed in the <strong>Default Child Delimiter</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="default-child-order-node-property-of-flat-file-schemas.md">Default Child Order</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the default relationship between delimiters and the data they delimit.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="default-escape-character-node-property-of-flat-file-schemas.md">Default Escape Character</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies a character to be used as the default escape character throughout an instance message. An escape character causes the following character to be interpreted as simple data, and not have the special meaning otherwise associated with it.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="default-escape-character-type-node-property-of-flat-file-schemas.md">Default Escape Character Type</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies how an alternative default escape character will be expressed in the <strong>Default Escape Character</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="default-repeating-delimiter-node-property-of-flat-file-schemas.md">Default Repeating Delimiter</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the default string used to delimit repeating fields in the record(s) in an instance message.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="default-repeating-delimiter-type-node-property-of-flat-file-schemas.md">Default Repeating Delimiter Type</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies how a default alternative repeating delimiter string will be expressed in the <strong>Default Repeating Delimiter</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="default-wrap-character-node-property-of-flat-file-schemas.md">Default Wrap Character</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies a character to be used as the default wrap character throughout an instance message. Wrap characters cause the characters that occur between them to be interpreted as simple data, and to not have the special meaning otherwise associated with them.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="default-wrap-character-type-node-property-of-flat-file-schemas.md">Default Wrap Character Type</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies how an alternative wrap character will be expressed in the <strong>Default Wrap Character</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="escape-character-node-property-of-flat-file-schemas.md">Escape Character</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies a character to be used as the escape character for the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.<br />
<br />
An escape character causes the following character to be interpreted as simple data, and not have the special meaning otherwise associated with it.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="escape-character-type-node-property-of-flat-file-schemas.md">Escape Character Type</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies how an alternative escape character will be expressed in the <strong>Escape Character</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="justification-node-property-of-flat-file-schemas.md">Justification</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the left or right justification of the contents of the field(s) that correspond to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="minimum-length-with-pad-character-node-property-of-flat-file-schemas.md">Minimum Length with Pad Character</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies how a serializer pads the data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td>Pad Character](../Topic/Pad%20Character%20(Node%20Property%20of%20Flat%20File%20Schemas).md)</td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the pad character to be used for data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="pad-character-type-node-property-of-flat-file-schemas.md">Pad Character Type</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies how an alternative pad character will be expressed in the <strong>Pad Character</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="positional-length-node-property-of-flat-file-schemas.md">Positional Length</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the length, from the previous sibling or delimiter, of the field in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="positional-offset-node-property-of-flat-file-schemas.md">Positional Offset</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the starting offset, relative to the previous sibling or delimiter, of the field in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="preserve-delimiter-for-empty-data-node-property-of-flat-file-schemas.md">Preserve Delimiter For Empty Data</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies whether the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node will have delimiters for empty fields and subordinate records.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="repeating-delimiter-node-property-of-flat-file-schemas.md">Repeating Delimiter</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the string used to delimit repeating fields and subordinate records in the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="repeating-delimiter-type-node-property-of-flat-file-schemas.md">Repeating Delimiter Type</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies how an alternative repeating delimiter string will be expressed in the <strong>Repeating Delimiter</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="restricted-characters-node-property-of-flat-file-schemas.md">Restricted Characters</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies ranges of characters that are restricted in instance messages.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="structure-node-property-of-flat-file-schemas.md">Structure</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies whether the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node is positional or delimited.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="suppress-trailing-delimiters-node-property-of-flat-file-schemas.md">Suppress Trailing Delimiters</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies whether trailing delimiters will be suppressed when output instance messages are serialized.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="tag-identifier-node-property-of-flat-file-schemas.md">Tag Identifier</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies an identifying tag for the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="tag-offset-node-property-of-flat-file-schemas.md">Tag Offset</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the starting offset of the tag, relative to the previous sibling or delimiter, for the record(s) in an instance message that corresponds to the selected <strong>Record</strong> node.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="odd">
<td><a href="wrap-character-node-property-of-flat-file-schemas.md">Wrap Character</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies a character to be used as the wrap character for the field(s) in an instance message that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Wrap characters cause the characters that occur between them to be interpreted as simple data, and to not have the special meaning otherwise associated with them.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
<tr class="even">
<td><a href="wrap-character-type-node-property-of-flat-file-schemas.md">Wrap Character Type</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies how an alternative wrap character will be expressed in the <strong>Wrap Character</strong> property and in the underlying XSD representation.<br />
<br />
Property category: <strong>Flat File</strong></td>
</tr>
</tbody>
</table>


## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

