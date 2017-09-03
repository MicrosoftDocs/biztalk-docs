---
title: "Schema Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a51bf02-c636-4edd-ad43-cc0dcebc28f5
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Node Properties

## Schema properties categories
When you select the **Schema** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. All schemas share a set of properties that are divided into the following categories:  
  
-   **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as data type derivations.  
  
-   **BizTalk.** This category contains properties that are related to processing and usability features that are specific to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the data type of the corresponding element or attribute.  
  
-   **Reference.** This category contains properties that are related to categorizing the business purpose of the schema and the industry standards to which it conforms.  
  
 Many of the properties associated with **Schema** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
> [!NOTE]
>  Some **Schema** node properties are automatically enabled or disabled, or shown or hidden, depending on the values of other node properties.  

## Schema node properties - all schemas  
 The following table shows the properties that are associated with the **Schema** node, and that are available in all schemas.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Attribute FormDefault](../core/attribute-formdefault-node-property-of-all-schemas.md)|Advanced|Specifies whether locally declared attributes must be qualified by using a namespace identifier throughout instance messages.|  
|[BlockDefault](../core/blockdefault-node-property-of-all-schemas.md)|Advanced|Specifies the default setting for whether or not derivations are permitted throughout the schema, and if so, which kinds (extension, restriction, and so on).|  
|[CodeList Database](../core/codelist-database-node-property-of-all-schemas.md)|BizTalk|Specifies the name and location of the database containing code lists used to set enumeration values at design-time.|  
|[Document Type](../core/document-type-node-property-of-all-schemas.md)|Reference|Specifies the type of schema that you are configuring, using whatever document type specification makes sense for your business.|  
|[Document Version](../core/document-version-node-property-of-all-schemas.md)|Reference|Specifies the version of the schema that you are configuring, using whatever versioning scheme makes sense for your business.|  
|[Element FormDefault](../core/element-formdefault-node-property-of-all-schemas.md)|Advanced|Specifies whether locally declared elements must be qualified by using a namespace identifier throughout instance messages.|  
|[Envelope](../core/envelope-node-property-of-all-schemas.md)|Reference|Specifies whether the schema represents an envelope.|  
|[FinalDefault](../core/finaldefault-node-property-of-all-schemas.md)|Advanced|Specifies whether a type can be used as the basis for particular types of derivations.|  
|[Imports](../core/imports-node-property-of-all-schemas.md)|Advanced|Specifies all of the namespaces that are used in the schema and provides the interface for importing, including, and redefining other schemas within the schema being edited.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Displays the name of the node as it appears in the schema tree view.|  
|[Promote Properties](../core/promote-properties-node-property-of-all-schemas.md)|BizTalk|Opens the **Promote Properties** dialog box in which you can specify the properties that you want to promote to the property context container.|  
|[Receipt](../core/receipt-node-property-of-all-schemas.md)|Reference|Specifies whether the schema represents an inbound receipt message.|  
|[Root Reference](../core/root-reference-node-property-of-all-schemas.md)|Reference|Specifies the node that represents the outermost element in the XML business document represented by the schema, and is important when you have created more than one top-level node in the schema.|  
|[Schema Editor Extensions](../core/schema-editor-extensions-node-property-of-all-schemas.md)|Advanced|Allows selection of the BizTalk Editor extensions to be associated with the selected schema.|  
|[Schema File Location](../core/schema-file-location-node-property-of-all-schemas.md)|General|Displays the file system location of the schema file associated with the schema being edited.|  
|[Schema Type](../core/schema-type-node-property-of-all-schemas.md)|Reference|Specifies the type of the selected schema as either a document schema or a property schema.|  
|[Specification Name](../core/specification-name-node-property-of-all-schemas.md)|Reference|Specifies a business name for the schema.|  
|[Standard](../core/standard-node-property-of-all-schemas.md)|Reference|Specifies the format and/or syntax of the instance message.|  
|[Standard Version](../core/standard-version-node-property-of-all-schemas.md)|Reference|Specifies the version of the format and/or syntax of the instance message, if appropriate.|  
|[Target Namespace](../core/target-namespace-node-property-of-all-schemas.md)|General|Specifies the target namespace for the schema using any valid uniform resource identifier (URI).|  
  
 When you select the **Schema** node in BizTalk Editor and you have enabled the **Flat File Extension** using the [Schema Editor Extensions](../core/schema-editor-extensions-node-property-of-all-schemas.md) property, you can examine and set additional properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the existing category **Reference** andthe new category **Flat File**, the latter of which contains those properties related to parsing flat files in equivalent XML files and serializing XML files back into flat files.  

## Schema node properties - flat file  
 The following table shows the supplemental properties that are available for the **Schema** node when the **Flat File Extension** is enabled.  
  
|Flat file property name|Category|Description|  
|-----------------------------|--------------|-----------------|  
|Case|Flat File|Specifies whether data in instance messages should be converted to all uppercase, converted to all lowercase, or left as is.|  
|Code Page|Flat File|Specifies the code page to use with an instance message.|  
|Count Positions In Bytes|Reference|Specifies whether the positions will be counted in bytes.|  
|Default Child Delimiter|Flat File|Specifies the default string used to delimit fields and subordinate records in instance data.|  
|Default Child Delimiter Type|Flat File|Specifies how an alternative default child delimiter string will be expressed in the **Default Child Delimiter** property and in the underlying XSD representation.|  
|Default Child Order|Flat File|Specifies the default relationship between delimiters and the data they delimit.|  
|Default Escape Character|Flat File|Specifies a character to be used as the default escape character throughout an instance message. An escape character causes the following character to be interpreted as simple data, and not have the special meaning otherwise associated with it.|  
|Default Escape Character Type|Flat File|Specifies how an alternative default escape character will be expressed in the **Default Escape Character** property and in the underlying XSD representation.|  
|Default Repeating Delimiter|Flat File|Specifies the default string used to delimit repeating fields and subordinate records in instance data.|  
|Default Repeating Delimiter Type|Flat File|Specifies how a default alternative repeating delimiter string will be expressed in the **Default Repeating Delimiter** property and in the underlying XSD representation.|  
|Default Wrap Character|Flat File|Specifies a character to be used as the default wrap character throughout an instance message. Wrap characters cause the characters that occur between them to be interpreted as simple data, and not have the special meaning otherwise associated with it.|  
|Default Wrap Character Type|Flat File|Specifies how an alternative wrap character will be expressed in the **Default Wrap Character** property and in the underlying XSD representation.|  
|Restricted Characters|Reference|Specifies ranges of characters that are restricted in instance messages.|  

More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 The following table lists additional flat file node properties that do not appear in the Schema Editor. Using these properties requires hand editing the schema file in a text editor.  
  
|Property|Values|Default Value|Description|  
|--------------|------------|-------------------|-----------------|  
|suppress_empty_nodes|**true** or **false**|**false**|Indicates whether or not to remove empty XML nodes after the parser generates XML instance data.|  
|generate_empty_nodes|**true** or **false**|**true**|Generate empty nodes for records that exist in the XML instance data.|  
|parser_optimization|**speed** or **complexity**|**speed**|Optimizing for speed decreases the parsing time but at the cost of dealing with some ambiguities in data. Optimizing for complexity handles a wider range of ambiguities but at the cost of processing speed.|  
|lookahead_depth|Any positive integer; zero (0) indicates infinite lookahead.|3|How far to look ahead for matching data.|  
|allow_early_termination|**true** or **false**|**false**|Indicates whether positional records can terminate early (**true**) or must contain data for all record fields (**false**).|  
|early_terminate_optional_fields|**true** or **false**|**false**|Enable early termination of optional trailing fields (**true**). If the existing schema without this annotation is opened in the BizTalk Editor, this annotation will be added to it with the default value set to (**false**). **Note:**  The early_terminate_optional_fields annotation only takes effect if the allow_early_termination is set to (**true**).|  
  
 All of these properties are attributes of the **/annotation/appinfo/schemaInfo** element.  
  
 When **parser_optimization** is set to **complexity**, you may have validation failures against a schema when there are many optional nodes in the same group or record. You may need to set **lookahead_depth** to zero (0) to avoid validation errors.  
  
## See Also  
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)