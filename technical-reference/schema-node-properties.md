---
title: Schema Node Properties
TOCTitle: Schema Node Properties
ms:assetid: 2a51bf02-c636-4edd-ad43-cc0dcebc28f5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559329(v=BTS.80)
ms:contentKeyID: 51527000
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Schema Node Properties

 

When you select the **Schema** node in BizTalk Editor, you can examine and set its associated properties in the Visual Studio Properties window. All schemas share a set of properties that are divided into the following categories:

  - **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as data type derivations.

  - **BizTalk.** This category contains properties that are related to processing and usability features that are specific to Microsoft BizTalk Server.

  - **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the data type of the corresponding element or attribute.

  - **Reference.** This category contains properties that are related to categorizing the business purpose of the schema and the industry standards to which it conforms.

Many of the properties associated with **Schema** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).


> [!NOTE]
> <P>Some <STRONG>Schema</STRONG> node properties are automatically enabled or disabled, or shown or hidden, depending on the values of other node properties.</P>



The following table shows the properties that are associated with the **Schema** node, and that are available in all schemas.

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
<td><a href="attribute-formdefault-node-property-of-all-schemas.md">Attribute FormDefault</a></td>
<td>Advanced</td>
<td>Specifies whether locally declared attributes must be qualified by using a namespace identifier throughout instance messages.</td>
</tr>
<tr class="even">
<td><a href="blockdefault-node-property-of-all-schemas.md">BlockDefault</a></td>
<td>Advanced</td>
<td>Specifies the default setting for whether or not derivations are permitted throughout the schema, and if so, which kinds (extension, restriction, and so on).</td>
</tr>
<tr class="odd">
<td><a href="codelist-database-node-property-of-all-schemas.md">CodeList Database</a></td>
<td>BizTalk</td>
<td>Specifies the name and location of the database containing code lists used to set enumeration values at design-time.</td>
</tr>
<tr class="even">
<td><a href="document-type-node-property-of-all-schemas.md">Document Type</a></td>
<td>Reference</td>
<td>Specifies the type of schema that you are configuring, using whatever document type specification makes sense for your business.</td>
</tr>
<tr class="odd">
<td><a href="document-version-node-property-of-all-schemas.md">Document Version</a></td>
<td>Reference</td>
<td>Specifies the version of the schema that you are configuring, using whatever versioning scheme makes sense for your business.</td>
</tr>
<tr class="even">
<td><a href="element-formdefault-node-property-of-all-schemas.md">Element FormDefault</a></td>
<td>Advanced</td>
<td>Specifies whether locally declared elements must be qualified by using a namespace identifier throughout instance messages.</td>
</tr>
<tr class="odd">
<td><a href="envelope-node-property-of-all-schemas.md">Envelope</a></td>
<td>Reference</td>
<td>Specifies whether the schema represents an envelope.</td>
</tr>
<tr class="even">
<td><a href="finaldefault-node-property-of-all-schemas.md">FinalDefault</a></td>
<td>Advanced</td>
<td>Specifies whether a type can be used as the basis for particular types of derivations.</td>
</tr>
<tr class="odd">
<td><a href="imports-node-property-of-all-schemas.md">Imports</a></td>
<td>Advanced</td>
<td>Specifies all of the namespaces that are used in the schema and provides the interface for importing, including, and redefining other schemas within the schema being edited.</td>
</tr>
<tr class="even">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td>General</td>
<td>Displays the name of the node as it appears in the schema tree view.</td>
</tr>
<tr class="odd">
<td><a href="promote-properties-node-property-of-all-schemas.md">Promote Properties</a></td>
<td>BizTalk</td>
<td>Opens the <strong>Promote Properties</strong> dialog box in which you can specify the properties that you want to promote to the property context container.</td>
</tr>
<tr class="even">
<td><a href="receipt-node-property-of-all-schemas.md">Receipt</a></td>
<td>Reference</td>
<td>Specifies whether the schema represents an inbound receipt message.</td>
</tr>
<tr class="odd">
<td><a href="root-reference-node-property-of-all-schemas.md">Root Reference</a></td>
<td>Reference</td>
<td>Specifies the node that represents the outermost element in the XML business document represented by the schema, and is important when you have created more than one top-level node in the schema.</td>
</tr>
<tr class="even">
<td><a href="schema-editor-extensions-node-property-of-all-schemas.md">Schema Editor Extensions</a></td>
<td>Advanced</td>
<td>Allows selection of the BizTalk Editor extensions to be associated with the selected schema.</td>
</tr>
<tr class="odd">
<td><a href="schema-file-location-node-property-of-all-schemas.md">Schema File Location</a></td>
<td>General</td>
<td>Displays the file system location of the schema file associated with the schema being edited.</td>
</tr>
<tr class="even">
<td><a href="schema-type-node-property-of-all-schemas.md">Schema Type</a></td>
<td>Reference</td>
<td>Specifies the type of the selected schema as either a document schema or a property schema.</td>
</tr>
<tr class="odd">
<td><a href="specification-name-node-property-of-all-schemas.md">Specification Name</a></td>
<td>Reference</td>
<td>Specifies a business name for the schema.</td>
</tr>
<tr class="even">
<td><a href="standard-node-property-of-all-schemas.md">Standard</a></td>
<td>Reference</td>
<td>Specifies the format and/or syntax of the instance message.</td>
</tr>
<tr class="odd">
<td><a href="standard-version-node-property-of-all-schemas.md">Standard Version</a></td>
<td>Reference</td>
<td>Specifies the version of the format and/or syntax of the instance message, if appropriate.</td>
</tr>
<tr class="even">
<td><a href="target-namespace-node-property-of-all-schemas.md">Target Namespace</a></td>
<td>General</td>
<td>Specifies the target namespace for the schema using any valid uniform resource identifier (URI).</td>
</tr>
</tbody>
</table>


When you select the **Schema** node in BizTalk Editor and you have enabled the **Flat File Extension** using the [Schema Editor Extensions](schema-editor-extensions-node-property-of-all-schemas.md) property, you can examine and set additional properties in the Visual Studio Properties window. These properties are divided into the existing category **Reference** andthe new category **Flat File**, the latter of which contains those properties related to parsing flat files in equivalent XML files and serializing XML files back into flat files.

The following table shows the supplemental properties that are available for the **Schema** node when the **Flat File Extension** is enabled.

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
<td><a href="case-node-property-of-flat-file-schemas.md">Case</a></td>
<td>Flat File</td>
<td>Specifies whether data in instance messages should be converted to all uppercase, converted to all lowercase, or left as is.</td>
</tr>
<tr class="even">
<td><a href="code-page-node-property-of-flat-file-schemas.md">Code Page</a></td>
<td>Flat File</td>
<td>Specifies the code page to use with an instance message.</td>
</tr>
<tr class="odd">
<td><a href="count-positions-in-bytes-node-property-of-flat-file-schemas.md">Count Positions In Bytes</a></td>
<td>Reference</td>
<td>Specifies whether the positions will be counted in bytes.</td>
</tr>
<tr class="even">
<td><a href="default-child-delimiter-node-property-of-flat-file-schemas.md">Default Child Delimiter</a></td>
<td>Flat File</td>
<td>Specifies the default string used to delimit fields and subordinate records in instance data.</td>
</tr>
<tr class="odd">
<td><a href="default-child-delimiter-type-node-property-of-flat-file-schemas.md">Default Child Delimiter Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative default child delimiter string will be expressed in the <strong>Default Child Delimiter</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="even">
<td><a href="default-child-order-node-property-of-flat-file-schemas.md">Default Child Order</a></td>
<td>Flat File</td>
<td>Specifies the default relationship between delimiters and the data they delimit.</td>
</tr>
<tr class="odd">
<td><a href="default-escape-character-node-property-of-flat-file-schemas.md">Default Escape Character</a></td>
<td>Flat File</td>
<td>Specifies a character to be used as the default escape character throughout an instance message. An escape character causes the following character to be interpreted as simple data, and not have the special meaning otherwise associated with it.</td>
</tr>
<tr class="even">
<td><a href="default-escape-character-type-node-property-of-flat-file-schemas.md">Default Escape Character Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative default escape character will be expressed in the <strong>Default Escape Character</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="odd">
<td><a href="default-repeating-delimiter-node-property-of-flat-file-schemas.md">Default Repeating Delimiter</a></td>
<td>Flat File</td>
<td>Specifies the default string used to delimit repeating fields and subordinate records in instance data.</td>
</tr>
<tr class="even">
<td><a href="default-repeating-delimiter-type-node-property-of-flat-file-schemas.md">Default Repeating Delimiter Type</a></td>
<td>Flat File</td>
<td>Specifies how a default alternative repeating delimiter string will be expressed in the <strong>Default Repeating Delimiter</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="odd">
<td><a href="default-wrap-character-node-property-of-flat-file-schemas.md">Default Wrap Character</a></td>
<td>Flat File</td>
<td>Specifies a character to be used as the default wrap character throughout an instance message. Wrap characters cause the characters that occur between them to be interpreted as simple data, and not have the special meaning otherwise associated with it.</td>
</tr>
<tr class="even">
<td><a href="default-wrap-character-type-node-property-of-flat-file-schemas.md">Default Wrap Character Type</a></td>
<td>Flat File</td>
<td>Specifies how an alternative wrap character will be expressed in the <strong>Default Wrap Character</strong> property and in the underlying XSD representation.</td>
</tr>
<tr class="odd">
<td><a href="restricted-characters-node-property-of-flat-file-schemas.md">Restricted Characters</a></td>
<td>Reference</td>
<td>Specifies ranges of characters that are restricted in instance messages.</td>
</tr>
</tbody>
</table>


The following table lists additional flat file node properties that do not appear in the Schema Editor. Using these properties requires hand editing the schema file in a text editor.

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Values</th>
<th>Default Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>suppress_empty_nodes</td>
<td><strong>true</strong> or <strong>false</strong></td>
<td><strong>false</strong></td>
<td>Indicates whether or not to remove empty XML nodes after the parser generates XML instance data.</td>
</tr>
<tr class="even">
<td>generate_empty_nodes</td>
<td><strong>true</strong> or <strong>false</strong></td>
<td><strong>true</strong></td>
<td>Generate empty nodes for records that exist in the XML instance data.</td>
</tr>
<tr class="odd">
<td>parser_optimization</td>
<td><strong>speed</strong> or <strong>complexity</strong></td>
<td><strong>speed</strong></td>
<td>Optimizing for speed decreases the parsing time but at the cost of dealing with some ambiguities in data. Optimizing for complexity handles a wider range of ambiguities but at the cost of processing speed.</td>
</tr>
<tr class="even">
<td>lookahead_depth</td>
<td>Any positive integer; zero (0) indicates infinite lookahead.</td>
<td>3</td>
<td>How far to look ahead for matching data.</td>
</tr>
<tr class="odd">
<td>allow_early_termination</td>
<td><strong>true</strong> or <strong>false</strong></td>
<td><strong>false</strong></td>
<td>Indicates whether positional records can terminate early (<strong>true</strong>) or must contain data for all record fields (<strong>false</strong>).</td>
</tr>
<tr class="even">
<td>early_terminate_optional_fields</td>
<td><strong>true</strong> or <strong>false</strong></td>
<td><strong>false</strong></td>
<td>Enable early termination of optional trailing fields (<strong>true</strong>). If the existing schema without this annotation is opened in the BizTalk Editor, this annotation will be added to it with the default value set to (<strong>false</strong>). <strong>Note:</strong> The early_terminate_optional_fields annotation only takes effect if the allow_early_termination is set to (<strong>true</strong>).</td>
</tr>
</tbody>
</table>


All of these properties are attributes of the **/annotation/appinfo/schemaInfo** element.

When **parser\_optimization** is set to **complexity**, you may have validation failures against a schema when there are many optional nodes in the same group or record. You may need to set **lookahead\_depth** to zero (0) to avoid validation errors.

## See Also

[Node Properties - By Node Type](node-properties-by-node-type.md)  
[Node Properties - Alphabetical Listings](node-properties-alphabetical-listings.md)

