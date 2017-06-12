---
title: "Fixed (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fixed property [schemas]"
ms.assetid: 4edfb40c-6401-4f78-9851-119904d4b4c9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Fixed (Node Property of All Schemas)
Use the **Fixed** property to specify a fixed value for the corresponding element or attribute in an instance message; if the corresponding element or attribute is present in an instance message, it must have the specified "fixed" value in order to be valid.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
 Any value that conforms to the data type specified by the **Data Type** property.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 The value of this property, if any, is used as the value of the **fixed** attribute of the element that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 You cannot configure both the **Fixed** and **Default Value** properties because it is prohibited by XSD.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)