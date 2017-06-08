---
title: "Schema Editor Extensions (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schema Editor Extensions property [schemas]"
ms.assetid: 2fd636b1-903b-44c5-8808-3ca5e6b0de1f
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Editor Extensions (Node Property of All Schemas)
Use the **Schema Editor Extensions** property to select editor extensions to be associated with this schema.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comes with two built-in schema editor extensions, as follows:  
  
-   **Flat File Extension.** Use this extension for creating schemas that work with flat file instance messages that use special characters or fixed lengths to delimit the records and fields within them (in contrast to XML-based instance messages).  
  
-   **EDI Schema Editor Extension.** Use this extension for creating Electronic Data Interchange (EDI)schemas.  
  
 There can be an arbitrary number of schema editor extensions, either developed by you for your special schema editing needs, or perhaps installed by BizTalk Server adapters and other programs.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the of the **schema/annotation/appinfo/schemaInfo/schemaEditorExtension:schemaInfo** element and its various attributes.  
  
 In addition, when the **Flat File Extension** or **EDI Schema Editor Extension** is enabled, the [Standard](../core/standard-node-property-of-all-schemas.md) property is set to **Flat File** or **EDI**, respectively.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 You can select schema editor extensions by clicking the ellipsis (**...**) button located to the right of the **Schema Editor Extensions** property value field to open the **Schema Editor Extensions** dialog box. In this dialog box, you can select the check boxes for the schema editor extensions that you want to enable.  
  
 To be able to develop schemas for flat files, you must use this property to include the **Flat File Extension**. This extension adds its own set of node properties, which are stored as annotations with the XSD representation of the schema. For more information, see [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md).  
  
> [!NOTE]
>  More than one schema extension can be chosen at a time. The same schema can represent both a flat file as well as, for example, an EDI schema. In such cases, the [Standard](../core/standard-node-property-of-all-schemas.md) property of the **Schema** node, which is generally set to a value that indicates the extension in use, should be set to the most active extension. The **Standard** property is used by BizTalk Editor to drive the functions that validate schemas and instance messages, and generate instance messages.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)