---
title: "Field Attribute Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "field attribute node properties [schemas]"
  - "schema node types, field attributes"
  - "Flat File Extension, properties"
ms.assetid: aea31ecf-ef0b-47a8-844f-2175b6ea1c90
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Field Attribute Node Properties
When you select a **Field Attribute** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the following categories:  
  
-   **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as data type derivations.  
  
-   **BizTalk.** This category contains properties that are related to usability and annotation features that are specific to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the data type of the corresponding element or attribute.  
  
-   **Restricted.** This category contains properties that correspond to XSD concepts related to type derivations through restriction.  
  
 When you insert a **Field Attribute** node, the name of the node as displayed in the schema tree, and which corresponds to its **Node Name** property, is immediately made available for editing within the schema tree. Your choice of a name for this node is important because it defines the name of the corresponding XML attribute in the instance messages that this schema defines.  
  
 Many of the properties associated with **Field Attribute** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs. For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
> [!NOTE]
>  Some **Field Attribute** node properties are automatically enabled or disabled, or shown or hidden, depending on the values of other node properties.  
  
 The following table shows the properties associated with **Field Attribute** nodes that are available in all schemas.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Base Data Type](../core/base-data-type-node-property-of-all-schemas.md)|Advanced|Specifies the base data type from which the type for the selected **Field Attribute** node is derived.|  
|[CodeList](../core/codelist-node-property-of-all-schemas.md)|BizTalk|Specifies the reference number for the code list to use with the selected **Field Attribute** node and provides access to the **CodeList** dialog box.|  
|[Data Type](../core/data-type-node-property-of-all-schemas.md)|General|Specifies the name of an existing data type for the selected **Field Attribute** node or specifies a name for this data type that can be used elsewhere.|  
|[Default Value](../core/default-value-node-property-of-all-schemas.md)|General|Specifies the default value for the selected **Field Attribute** node.|  
|[Derived By](../core/derived-by-node-property-of-all-schemas.md)|Advanced|Specifies how the underlying simple type of this **Field Attribute** node is derived from its base type (by Restriction, List, or Union).|  
|[Enumeration](../core/enumeration-node-property-of-all-schemas.md)|Restricted|Limits any data in an instance message corresponding to the selected **Field Attribute** node to a specific set of values.|  
|[Field Type](../core/field-type-node-property-of-all-schemas.md)|General|Identifies the selected **Field Attribute** node as a **Field Attribute** node as opposed to a **Field Element** node.|  
|[Final](../core/final-node-property-of-all-schemas.md)|Advanced|Specifies derivation restrictions for the data type defined for the selected **Field Attribute** node.|  
|[Fixed](../core/fixed-node-property-of-all-schemas.md)|Advanced|Specifies a fixed value for the attribute(s) in an instance message that corresponds to the selected **Field Attribute** node, if the data is present.|  
|[Form](../core/form-node-property-of-all-schemas.md)|Advanced|Specifies whether local attributes in instance messages must be qualified with a namespace identifier.|  
|[Instance XPath](../core/instance-xpath-node-property-of-all-schemas.md)|General|Displays the location within instance messages of the attribute that corresponds to the selected **Field Attribute** node.|  
|[Item Type](../core/item-type-node-property-of-all-schemas.md)|Advanced|Specifies the data type of the corresponding attribute(s) in instance messages when the **Derived By** property is set to **List**.|  
|[Length](../core/length-node-property-of-all-schemas.md)|Restricted|Specifies the fixed length of the data corresponding to the selected **Field Attribute** node in instance messages.|  
|[MaxFacet Type](../core/maxfacet-type-node-property-of-all-schemas.md)|Restricted|Specifies whether the upper bound of the ordered value for any data in instance messages that corresponds to the selected **Field Attribute** node, as specified by the **MaxFacet Value** property, is inclusive or exclusive.|  
|[MaxFacet Value](../core/maxfacet-value-node-property-of-all-schemas.md)|Restricted|Specifies the maximum value (inclusive or exclusive, as specified by the **MaxFacet Type** property) for any data in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Maximum Length](../core/maximum-length-node-property-of-all-schemas.md)|Restricted|Specifies the maximum length for data in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Member Types](../core/member-types-node-property-of-all-schemas.md)|Advanced|Specifies the list of valid data types for the corresponding attribute(s) in instance messages when the **Derived By** property is set to **Union**.|  
|[MinFacet Type](../core/minfacet-type-node-property-of-all-schemas.md)|Restricted|Specifies whether the lower bound of the ordered value for any data in instance messages that corresponds to the selected **Field Attribute** node, as specified by the **MaxFacet Value** property, is inclusive or exclusive.|  
|[MinFacet Value](../core/minfacet-value-node-property-of-all-schemas.md)|Restricted|Specifies the minimum value (inclusive or exclusive, as specified by the **MinFacet Type** property) for any data in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Minimum Length](../core/minimum-length-node-property-of-all-schemas.md)|Restricted|Specifies the minimum length for data in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Displays the namespace for the selected **Field Attribute** node.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Specifies the name of the selected **Field Attribute** node as it appears in the schema tree view.|  
|[Notes](../core/notes-node-property-of-all-schemas.md)|BizTalk|Specifies notes about the selected **Field Attribute** node.|  
|[Pattern](../core/pattern-node-property-of-all-schemas.md)|Restricted|Limits any data in an instance message corresponding to the selected **Field Attribute** node to a specific pattern, as specified by one or more regular expressions.|  
|[Use Requirement](../core/use-requirement-node-property-of-all-schemas.md)|General|Specifies whether the attribute that corresponds to the selected **Field Attribute** node is required in an instance message.|  
  
 When you select a **Field Attribute** node in BizTalk Editor and you have enabled the **Flat File Extension** using the [Schema Editor Extensions](../core/schema-editor-extensions-node-property-of-all-schemas.md) property, you can examine and set additional properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the existing category **Reference** and the new category **Flat File**, the latter of which contains those properties related to parsing flat files in equivalent XML files and serializing XML files back into flat files.  
  
 The following table shows the supplemental properties that are available for **Field Attribute** nodes when the **Flat File Extension** is enabled.  
  
|Flat file property name|Category|Description|  
|-----------------------------|--------------|-----------------|  
|[Custom Date/Time Format](../core/custom-date-time-format-node-property-of-flat-file-schemas.md)|Flat File|Specifies the format for your custom date/time type when the selected **Field Element** node is set to one of the following XSD data types or a simple type derived from one of them: **Note:**  xs:date, xs:dateTime, xs:time, xs:gYearMonth, xs:gYear, xs:gMonthDay, xs:gDay, or xs:gMonth|  
|[Justification](../core/justification-node-property-of-flat-file-schemas.md)|Flat File|Specifies the left or right justification of the contents of the field(s) that correspond to the selected **Field Attribute** node.|  
|[Minimum Length with Pad Character](../core/minimum-length-with-pad-character-node-property-of-flat-file-schemas.md)|Flat File|Specifies how a serializer pads the data in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Pad Character](../core/pad-character-node-property-of-flat-file-schemas.md)|Flat File|Specifies the pad character to be used for data in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Pad Character Type](../core/pad-character-type-node-property-of-flat-file-schemas.md)|Flat File|Specifies how an alternative pad character will be expressed in the **Pad Character** property and in the underlying XSD representation.|  
|[Positional Length](../core/positional-length-node-property-of-flat-file-schemas.md)|Reference|Specifies the length, from the previous sibling or delimiter, of the field in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Positional Offset](../core/positional-offset-node-property-of-flat-file-schemas.md)|Reference|Specifies the starting offset, relative to the previous sibling or delimiter, of the field in instance messages that corresponds to the selected **Field Attribute** node.|  
|[Wrap Character](../core/wrap-character-node-property-of-flat-file-schemas.md)|Flat File|Specifies a character to be used as the wrap character for the field(s) in an instance message that corresponds to the selected **Field Attribute** node.<br /><br /> Wrap characters cause the characters that occur between them to be interpreted as simple data, and to not have the special meaning otherwise associated with it.|  
|[Wrap Character Type](../core/wrap-character-type-node-property-of-flat-file-schemas.md)|Flat File|Specifies how an alternative wrap character will be expressed in the **Wrap Character** property and in the underlying XSD representation.|  
  
## See Also  
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)