---
title: "Base Data Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Base Data Type property [schemas]"
ms.assetid: 17972a21-fe2e-4968-ab94-89f87d6b93f6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Base Data Type (Node Property of All Schemas)
Use the **Base Data Type** property to specify the base data type value from which the data type of the selected **Record**, **Field Element**, or **Field Attribute** node will be derived (for example, "xs:string").  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
 No value, or any of the data types shown in the drop-down list for this property.  
  
## Default Value  
 Blank, indicating that the data type of this **Record**, **Field Element**, or **Field Attribute** node is not derived from another data type.  
  
## XSD Persistence  
 As the value of the **base** attribute of the **extension**, **restriction**, **list**, or **union** element within the element(s) that corresponds to the selected **Record**, **Field Element**,or **Field Attribute** node. For more information about the persistence permutations, see the XSD Persistence section of [Derived By (Node Property of All Schemas)](../core/derived-by-node-property-of-all-schemas.md).  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** (including a root **Record** node), **Field Element**, or **Field Attribute** node in BizTalk Editor.  
  
 The setting of this property interacts with the [Content Type](../core/content-type-node-property-of-all-schemas.md) (**Record** nodes only) and [Derived By](../core/derived-by-node-property-of-all-schemas.md) properties.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)