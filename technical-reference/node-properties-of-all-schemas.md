---
title: Node Properties of All Schemas
TOCTitle: Node Properties of All Schemas
ms:assetid: 893c7352-7c18-4771-a9b6-e93239fe7d64
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561245(v=BTS.80)
ms:contentKeyID: 51529512
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Node Properties of All Schemas

 

This section provides an alphabetically organized set of reference topics for the node properties that are available within all schemas (with a few noted exceptions).

Because different properties can apply to one, some, or all types of nodes, the following table and each node property reference topic contains a column or section that indicates the node types to which the property applies.

Many of the properties associated with all nodes in schemas correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).

The following table shows the nodes properties that are available in all schemas.

<table>
<thead>
<tr class="header">
<th>Property name</th>
<th>Applies to node type(s)</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="attribute-formdefault-node-property-of-all-schemas.md">Attribute FormDefault</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether locally declared attributes must be qualified by using a namespace identifier in instance messages.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="base-data-type-node-property-of-all-schemas.md">Base Data Type</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the base data type from which the type for the selected node is derived.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="base-type-node-property-of-all-schemas.md">Base Type</a></td>
<td><a href="equivalent-node-properties.md">Equivalent</a></td>
<td>Shows the base complex type from which the other complex types shown as child nodes of the <strong>Equivalent</strong> node are derived.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="block-node-property-of-all-schemas.md">Block</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Prevents or defines allowed derivations of this <strong>Record</strong> node in other schemas.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td><a href="blockdefault-node-property-of-all-schemas.md">BlockDefault</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the default setting for whether or not derivations are permitted throughout the schema, and if so, which kinds (extension, restriction, and so on).<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="body-xpath-node-property-of-all-schemas.md">Body XPath</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Identifies the portion of the schema that defines the body of the message associated with a root <strong>Record</strong> node in an envelope schema.<br />
<br />
Property category: <strong>Parse</strong></td>
</tr>
<tr class="odd">
<td><a href="codelist-node-property-of-all-schemas.md">CodeList</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the reference number for the code list to use with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node, and provides access to the <strong>CodeList</strong> dialog box.<br />
<br />
Property category: <strong>BizTalk</strong></td>
</tr>
<tr class="even">
<td><a href="codelist-database-node-property-of-all-schemas.md">CodeList Database</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the name and location of the database containing code lists used to set enumeration values at design-time.<br />
<br />
Property category: <strong>BizTalk</strong></td>
</tr>
<tr class="odd">
<td><a href="content-type-node-property-of-all-schemas.md">Content Type</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies whether the content of the <strong>Record</strong> node is simple or complex.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="data-structure-type-node-property-of-all-schemas.md">Data Structure Type</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies one of the following:<br />
<br />
- An existing data type for the selected <strong>Record</strong> node, by selecting the data type from the list.<br />
- A new global complex data type to be created for the selected <strong>Record</strong> node, by typing a name for the new data type.<br />
- That the selected <strong>Record</strong> node should refer to another global level <strong>Record</strong> node, by selecting &quot;<em>&lt;RecordName&gt;</em> (Reference)&quot; from the list.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td><a href="data-type-node-property-of-all-schemas.md">Data Type</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies a simple data type for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="default-value-node-property-of-all-schemas.md">Default Value</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the default value for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td><a href="derivation-type-node-property-of-all-schemas.md">Derivation Type</a></td>
<td><a href="equivalent-child-node-properties.md">Equivalent Child</a></td>
<td>Shows the base complex type or one of the derived complex types.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="derived-by-node-property-of-all-schemas.md">Derived By</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies how the complex type associated with the selected <strong>Record</strong> node is derived from the data type specified by the <strong>Base Data Type</strong> property.<br />
<br />
Or, specifies how the simple type associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node is derived from the data type specified by the <strong>Base Data Type</strong> property.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="document-type-node-property-of-all-schemas.md">Document Type</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the type of schema that you are configuring, using whatever document type specification makes sense for your business.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="document-version-node-property-of-all-schemas.md">Document Version</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the version of the schema that you are configuring, using whatever versioning scheme makes sense for your business.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="element-formdefault-node-property-of-all-schemas.md">Element FormDefault</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether locally declared elements must be qualified by using a namespace identifier in instance messages.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="enumeration-node-property-of-all-schemas.md">Enumeration</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Limits any data in an instance message corresponding to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node to a specific set of values.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="odd">
<td><a href="envelope-node-property-of-all-schemas.md">Envelope</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether the schema represents an envelope. Configure this property only if you are creating a flat file or an XML file.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="field-type-node-property-of-all-schemas.md">Field Type</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Identifies the selected node as a <strong>Field Element</strong> node or a <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td><a href="final-node-property-of-all-schemas.md">Final</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies derivation restrictions for the data type defined for the selected <strong>Record</strong>, <strong>Field Element</strong>, or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="finaldefault-node-property-of-all-schemas.md">FinalDefault</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether types defined in the schema being edited can be used as the basis for any derivations.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td>Fixed](../Topic/Fixed%20(Node%20Property%20of%20All%20Schemas).md)</td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies a fixed value for the element(s) or attribute in an instance message that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node, if the data is present.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="form-node-property-of-all-schemas.md">Form</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies whether local elements in instance messages must be qualified with a namespace identifier.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="group-max-occurs-node-property-of-all-schemas.md">Group Max Occurs</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the maximum number of times the underlying group content of the selected <strong>Record</strong> node can occur.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="group-min-occurs-node-property-of-all-schemas.md">Group Min Occurs</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the minimum number of times the underlying group content of the selected <strong>Record</strong> node can occur.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="group-order-type-node-property-of-all-schemas.md">Group Order Type</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies the type of group ordering of child nodes below the selected <strong>Record</strong> node.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="group-reference-node-property-of-all-schemas.md">Group Reference</a></td>
<td><a href="sequence-group-node-properties.md">Sequence Group</a>, <a href="choice-group-node-properties.md">Choice Group</a>, <a href="all-group-node-properties.md">All Group</a>, <a href="attribute-group-node-properties.md">Attribute Group</a></td>
<td>Specifies the globally defined group referenced by the selected <strong>Sequence Group</strong>, <strong>Choice Group</strong>, <strong>All Group</strong>, or <strong>Attribute Group</strong> node.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="imports-node-property-of-all-schemas.md">Imports</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies all of the namespaces that are used in the schema and provides the interface for importing, including, and redefining other schemas within the schema being edited.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="instance-xpath-node-property-of-all-schemas.md">Instance XPath</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a>, <a href="any-element-node-properties.md">Any Element</a>, <a href="any-attribute-node-properties.md">Any Attribute</a></td>
<td>Displays the location within instance messages of the element(s) or attribute(s) that corresponds to the selected node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td><a href="item-type-node-property-of-all-schemas.md">Item Type</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the data type of the corresponding element(s) or attribute(s) in instance messages when the <strong>Derived By</strong> property is set to <strong>List</strong>.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="length-node-property-of-all-schemas.md">Length</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the fixed length of the data corresponding to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node in instance messages.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="odd">
<td><a href="max-occurs-node-property-of-all-schemas.md">Max Occurs</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="sequence-group-node-properties.md">Sequence Group</a>, <a href="choice-group-node-properties.md">Choice Group</a>, <a href="all-group-node-properties.md">All Group</a>, <a href="any-element-node-properties.md">Any Element</a></td>
<td>Specifies the maximum number of times that the element(s) corresponding to the selected node can occur.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="maxfacet-type-node-property-of-all-schemas.md">MaxFacet Type</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies whether the upper bound of the ordered value for any data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node, as specified by the <strong>MaxFacet Value</strong> property, is inclusive or exclusive.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="odd">
<td><a href="maxfacet-value-node-property-of-all-schemas.md">MaxFacet Value</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the maximum value (inclusive or exclusive, as specified by the <strong>MaxFacet Type</strong> property) for any data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="even">
<td><a href="maximum-length-node-property-of-all-schemas.md">Maximum Length</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the maximum length for the data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="odd">
<td><a href="member-types-node-property-of-all-schemas.md">Member Types</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the list of valid data types for the corresponding element(s) or attribute(s) in instance messages when the <strong>Derived By</strong> property is set to <strong>Union</strong>.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="min-occurs-node-property-of-all-schemas.md">Min Occurs</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="sequence-group-node-properties.md">Sequence Group</a>, <a href="choice-group-node-properties.md">Choice Group</a>, <a href="all-group-node-properties.md">All Group</a>, <a href="any-element-node-properties.md">Any Element</a></td>
<td>Specifies the minimum number of times that the element(s) corresponding to the selected node can occur.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td>MinFacet Type](../Topic/MinFacet%20Type%20(Node%20Property%20of%20All%20Schemas).md)</td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies whether the lower bound of the ordered value for any data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node, as specified by the <strong>MinFacet Value</strong> property, is inclusive or exclusive.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="even">
<td><a href="minfacet-value-node-property-of-all-schemas.md">MinFacet Value</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the minimum value (inclusive or exclusive, as specified by the <strong>MinFacet Type</strong> property) for any data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="odd">
<td><a href="minimum-length-node-property-of-all-schemas.md">Minimum Length</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies the minimum length for the data in instance messages that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="even">
<td><a href="mixed-node-property-of-all-schemas.md">Mixed</a></td>
<td><a href="record-node-properties.md">Record</a></td>
<td>Specifies that character data or text can appear with subelements in the selected <strong>Record</strong> node.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="namespace-node-property-of-all-schemas.md">Namespace</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a>, <a href="sequence-group-node-properties.md">Sequence Group</a>, <a href="choice-group-node-properties.md">Choice Group</a>, <a href="all-group-node-properties.md">All Group</a>, <a href="attribute-group-node-properties.md">Attribute Group</a>, <a href="any-element-node-properties.md">Any Element</a>, <a href="any-attribute-node-properties.md">Any Attribute</a></td>
<td>Displays the namespace for the selected node. For <strong>Any Element</strong> and <strong>Any Attribute</strong> nodes, this property is editable so that a namespace can be specified.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="nillable-node-property-of-all-schemas.md">Nillable</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a></td>
<td>Specifies whether the <strong>nil</strong> attribute can be used at run time with the element that corresponds to the selected node to indicate that it is still valid even if it has no content.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="node-name-node-property-of-all-schemas.md">Node Name</a></td>
<td><a href="schema-node-properties.md">Schema</a>, <a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a>, <a href="sequence-group-node-properties.md">Sequence Group</a>, <a href="choice-group-node-properties.md">Choice Group</a>, <a href="all-group-node-properties.md">All Group</a>, <a href="attribute-group-node-properties.md">Attribute Group</a>, <a href="any-element-node-properties.md">Any Element</a>, <a href="any-attribute-node-properties.md">Any Attribute</a>, <a href="equivalent-node-properties.md">Equivalent</a>, <a href="equivalent-child-node-properties.md">Equivalent Child</a></td>
<td>Specifies (or just displays) the name of the selected node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="notes-node-property-of-all-schemas.md">Notes</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies notes about the selected <strong>Record</strong>, <strong>Field Element</strong>, or <strong>Field Attribute</strong> node to be made.<br />
<br />
Property category: <strong>BizTalk</strong></td>
</tr>
<tr class="odd">
<td><a href="order-type-node-property-of-all-schemas.md">Order Type</a></td>
<td><a href="sequence-group-node-properties.md">Sequence Group</a>, <a href="choice-group-node-properties.md">Choice Group</a>, <a href="all-group-node-properties.md">All Group</a></td>
<td>Specifies the type of the selected element group node: <strong>Sequence</strong>, <strong>Choice</strong>, or <strong>All</strong>.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="even">
<td><a href="pattern-node-property-of-all-schemas.md">Pattern</a></td>
<td><a href="field-element-node-properties.md">Field Element</a>, <a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Limits any data in an instance message corresponding to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node to a specific pattern, as specified by one or more regular expressions.<br />
<br />
Property category: <strong>Restricted</strong></td>
</tr>
<tr class="odd">
<td><a href="process-contents-node-property-of-all-schemas.md">Process Contents</a></td>
<td><a href="any-element-node-properties.md">Any Element</a>, <a href="any-attribute-node-properties.md">Any Attribute</a></td>
<td>Specifies the level of validation data for instance messages that corresponds to the selected <strong>Any Element</strong> or <strong>Any Attribute</strong> node.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="promote-properties-node-property-of-all-schemas.md">Promote Properties</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Opens the <strong>Promote Properties</strong> dialog box in which you can specify the properties that you want to promote to the property context container.<br />
<br />
Property category: <strong>BizTalk</strong></td>
</tr>
<tr class="odd">
<td><a href="receipt-node-property-of-all-schemas.md">Receipt</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies whether the schema represents an inbound receipt message.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="root-reference-node-property-of-all-schemas.md">Root Reference</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the node that represents the outermost element in the XML business document represented by the schema, and is important when you have created more than one top-level node in the schema.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="rootnode-typename-node-property-of-all-schemas.md">RootNode TypeName</a></td>
<td><a href="record-node-properties.md">Record</a>, <a href="field-element-node-properties.md">Field Element</a></td>
<td>Specifies the name that will be used when generating the .NET class name for the selected root <strong>Record</strong> or root <strong>Field Element</strong> node.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="schema-editor-extensions-node-property-of-all-schemas.md">Schema Editor Extensions</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Allows selection of the BizTalk Editor extensions to be associated with the selected schema.<br />
<br />
Property category: <strong>Advanced</strong></td>
</tr>
<tr class="odd">
<td><a href="schema-file-location-node-property-of-all-schemas.md">Schema File Location</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Shows the file system location of the schema file associated with the schema being edited.<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="even">
<td><a href="schema-type-node-property-of-all-schemas.md">Schema Type</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the type of the selected schema as either a document schema or a property schema.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="specification-name-node-property-of-all-schemas.md">Specification Name</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies a business name for the schema.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="standard-node-property-of-all-schemas.md">Standard</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the format and/or syntax of the instance message.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="odd">
<td><a href="standard-version-node-property-of-all-schemas.md">Standard Version</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the version of the format and/or syntax of the instance message, if appropriate.<br />
<br />
Property category: <strong>Reference</strong></td>
</tr>
<tr class="even">
<td><a href="target-namespace-node-property-of-all-schemas.md">Target Namespace</a></td>
<td><a href="schema-node-properties.md">Schema</a></td>
<td>Specifies the target namespace for the schema using any valid uniform resource identifier (URI).<br />
<br />
Property category: <strong>General</strong></td>
</tr>
<tr class="odd">
<td>Use Requirement](../Topic/Use%20Requirement%20(Node%20Property%20of%20All%20Schemas).md)</td>
<td><a href="field-attribute-node-properties.md">Field Attribute</a></td>
<td>Specifies whether the attribute that corresponds to the selected <strong>Field Attribute</strong> node is required in an instance message. This property represents a standard XSD construct and is persisted as &quot;required.&quot;<br />
<br />
Property category: <strong>General</strong></td>
</tr>
</tbody>
</table>

