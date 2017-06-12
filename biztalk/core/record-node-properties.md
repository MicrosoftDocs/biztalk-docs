---
title: "Record Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema node types, records"
  - "record node properties [schemas]"
  - "Flat File Extension, properties"
ms.assetid: 61d5b2f6-b600-437a-8031-f66d05f131d4
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Record Node Properties
When you select a **Record** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the following categories:  
  
-   **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as data type derivations.  
  
-   **BizTalk.** This category contains a property that is related to an annotation feature that is specific to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the data type of the corresponding element or attribute.  
  
-   **Parse.** This category contains a property related to unwrapping envelope content in instance messages.  
  
 When you insert a **Record** node, the name of the node as displayed in the schema tree, and which corresponds to its **Node Name** property, is immediately made available for editing within the schema tree. Your choice of a name for this node is particularly important because it defines the name of the corresponding XML element in the instance messages that this schema defines.  
  
 Many of the properties associated with **Record** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
> [!NOTE]
>  Some **Record** node properties are automatically enabled or disabled, or shown or hidden, depending on the values of other node properties.  
  
 The following table shows the properties associated with **Record** nodes that are available in all schemas.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Base Data Type](../core/base-data-type-node-property-of-all-schemas.md)|Advanced|Specifies the base data type from which the type for the selected **Record** node is derived.|  
|[Block](../core/block-node-property-of-all-schemas.md)|General|Prevents or defines allowed derivations of this **Record** node in other schemas.|  
|[Body XPath](../core/body-xpath-node-property-of-all-schemas.md)|Parse|Identifies the portion of the schema that defines the body of the message associated with the select root **Record** node in an envelope schema.|  
|[Content Type](../core/content-type-node-property-of-all-schemas.md)|Advanced|Specifies whether the content of the **Record** node is simple or complex.|  
|[Data Structure Type](../core/data-structure-type-node-property-of-all-schemas.md)|General|Specifies a name for the data type of the selected node so that it can be used elsewhere.|  
|[Derived By](../core/derived-by-node-property-of-all-schemas.md)|Advanced|Specifies how the complex type associated with the selected node is derived from the data type specified by the **Base Data Type** property.|  
|[Final](../core/final-node-property-of-all-schemas.md)|General|Specifies derivation restrictions for the data type defined for the selected **Record** node.|  
|[Form](../core/form-node-property-of-all-schemas.md)|Advanced|Specifies whether local elements in instance messages must be qualified with a namespace identifier.|  
|[Group Max Occurs](../core/group-max-occurs-node-property-of-all-schemas.md)|Advanced|Specifies the maximum number of times the underlying group content of the selected **Record** node can occur.|  
|[Group Min Occurs](../core/group-min-occurs-node-property-of-all-schemas.md)|Advanced|Specifies the minimum number of times the underlying group content of the selected **Record** node can occur.|  
|[Group Order Type](../core/group-order-type-node-property-of-all-schemas.md)|Advanced|Specifies the type of group ordering of child nodes below the selected **Record** node.|  
|[Instance XPath](../core/instance-xpath-node-property-of-all-schemas.md)|General|Displays the location within instance messages of the element that corresponds to the selected **Record** node.|  
|[Max Occurs](../core/max-occurs-node-property-of-all-schemas.md)|General|Specifies the maximum number of times that the element corresponding to the selected **Record** node can occur.|  
|[Min Occurs](../core/min-occurs-node-property-of-all-schemas.md)|General|Specifies the minimum number of times that the element corresponding to the selected **Record** node can occur.|  
|[Mixed](../core/mixed-node-property-of-all-schemas.md)|Advanced|Specifies that character data or text can appear with subelements in the selected **Record** node.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Displays the namespace for the selected **Record** node.|  
|[Nillable](../core/nillable-node-property-of-all-schemas.md)|Advanced|Specifies whether the **xsi:nil** attribute can be used at run time with the element that corresponds to the selected **Record** node to indicate that it is still valid even if it has no content.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Specifies the name of the selected **Record** node as it appears in the schema tree view.|  
|[Notes](../core/notes-node-property-of-all-schemas.md)|BizTalk|Specifies notes about the selected **Record** node.|  
|[RootNode TypeName](../core/rootnode-typename-node-property-of-all-schemas.md)|Reference|Specifies the name that will be used when generating the .NET class name for the selected top-level **Record** root node.|  
  
 When you select a **Record** node in BizTalk Editor and you have enabled the **Flat File Extension** using the [Schema Editor Extensions](../core/schema-editor-extensions-node-property-of-all-schemas.md) property, you can examine and set additional properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties belong to the **Flat File** category and contain those properties related to parsing flat files in equivalent XML files and serializing XML files back into flat files.  
  
 The following table shows the supplemental properties that are available for **Record** nodes when the **Flat File Extension** is enabled.  
  
|Flat file property name|Category|Description|  
|-----------------------------|--------------|-----------------|  
|[Child Delimiter](../core/child-delimiter-node-property-of-flat-file-schemas.md)|Flat File|Specifies the string used to delimit fields and subordinate records in the record(s) in an instance message that corresponds to the selected **Record** node.|  
|[Child Delimiter Type](../core/child-delimiter-type-node-property-of-flat-file-schemas.md)|Flat File|Specifies how an alternative child delimiter string will be expressed in the **Child Delimiter** property and in the underlying XSD representation.|  
|[Child Order](../core/child-order-node-property-of-flat-file-schemas.md)|Flat File|Specifies the relationship between delimiters and the data they delimit.|  
|[Escape Character](../core/escape-character-node-property-of-flat-file-schemas.md)|Flat File|Specifies a character to be used as the escape character for the record(s) in an instance message that corresponds to the selected **Record** node.<br /><br /> An escape character causes the following character to be interpreted as simple data, and to not have the special meaning otherwise associated with it.|  
|[Escape Character Type](../core/escape-character-type-node-property-of-flat-file-schemas.md)|Flat File|Specifies how an alternative escape character will be expressed in the **Escape Character** property and in the underlying XSD representation.|  
|[Preserve Delimiter For Empty Data](../core/preserve-delimiter-for-empty-data-node-property-of-flat-file-schemas.md)|Flat File|Specifies whether the record(s) in an instance message that corresponds to the selected **Record** node will have delimiters for empty fields and subordinate records.|  
|[Repeating Delimiter](../core/repeating-delimiter-node-property-of-flat-file-schemas.md)|Flat File|Specifies the string used to delimit repeating fields and subordinate records in the record(s) in an instance message that corresponds to the selected **Record** node.|  
|[Repeating Delimiter Type](../core/repeating-delimiter-type-node-property-of-flat-file-schemas.md)|Flat File|Specifies how an alternative repeating delimiter string will be expressed in the **Repeating Delimiter** property and in the underlying XSD representation.|  
|[Structure](../core/structure-node-property-of-flat-file-schemas.md)|Flat File|Specifies whether the record(s) in an instance message that corresponds to the selected **Record** node is positional or delimited.|  
|[Suppress Trailing Delimiters](../core/suppress-trailing-delimiters-node-property-of-flat-file-schemas.md)|Flat File|Specifies whether trailing delimiters will be suppressed when output instance messages are serialized.|  
|[Tag Identifier](../core/tag-identifier-node-property-of-flat-file-schemas.md)|Flat File|Specifies an identifying tag for the record(s) in an instance message that corresponds to the selected **Record** node.|  
|[Tag Offset](../core/tag-offset-node-property-of-flat-file-schemas.md)|Flat File|Specifies the starting offset of the tag, relative to the previous sibling or delimiter, for the record(s) in an instance message that corresponds to the selected **Record** node.|  
  
## See Also  
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)