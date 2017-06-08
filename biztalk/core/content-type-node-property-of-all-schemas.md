---
title: "Content Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Content Type property [schemas]"
ms.assetid: db67f54d-cb33-4a25-9893-8ddbca7f3fe2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Content Type (Node Property of All Schemas)
Use the **Content Type** property to define whether the content of the **Record** node is simple or complex. Simple content is data only, and complex content is subelements.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Use this value in conjunction with a blank value for the [Base Data Type](../core/base-data-type-node-property-of-all-schemas.md) property to indicate a default interpretation (defined by XSD) of complex content that restricts **anyType**.<br /><br /> A blank value for **Base Data Type** property forces this property to the **(Default)** value and setting this property to **(Default)** forces the **Base Data Type** property to a blank value.|  
|**ComplexContent**|Specifies that content in the selected **Record** node can include subelements.|  
|**SimpleContent**|Specifies that content in the selected **Record** node is derived from a simple type. This means that it can contain only attributes and text that conform to the derived data type. In other words, it cannot contain subelements.|  
  
## Default Value  
 **(Default)**, indicating that there is no specified content type for the element that corresponds to this **Record** node, indicating a default interpretation (defined by XSD) of complex content that restricts **anyType**.  
  
## XSD Persistence  
 When set to other than the default value, represented within the **complexType** element of the **Record** node using a nested pair of elements: an **extension** or **restriction** element within a **simpleContent** or **complexContent** element. The **base** attribute of the **extension** or **restriction** element is set to the value of the [Base Data Type](../core/base-data-type-node-property-of-all-schemas.md) property.  
  
 For more information about these persistence permutations, see the XSD Persistence section of [Derived By (Node Property of All Schemas)](../core/derived-by-node-property-of-all-schemas.md).  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.  
  
 The setting of this property interacts with the [Base Data Type](../core/base-data-type-node-property-of-all-schemas.md) and [Derived By](../core/derived-by-node-property-of-all-schemas.md) properties.  
  
 Simple content includes only attributes and text data. Complex content includes elements, attributes, and if the [Mixed](../core/mixed-node-property-of-all-schemas.md) property is set to **True**, text data.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)