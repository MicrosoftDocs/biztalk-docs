---
title: "Member Types (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Member Types property [schemas]"
ms.assetid: b5a657d2-0c01-47c2-81e0-ede74bf732d3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Member Types (Node Property of All Schemas)
Use the **Member Types** property to specify the data types that correspond to a **Derived By** property setting of **Union** for the selected **Field Element** or **Field Attribute** node, allowing corresponding data in instance messages to conform to any of the chosen data types.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
 Any combination of the simple data types available in the drop-down list for this property.  
  
## Default Value  
 xs:string  
  
## XSD Persistence  
 As the value of the **memberTypes** attribute of the **simpleType/union** elements within the element that corresponds to the selected **Field Element** or **Field Attribute** node. If multiple data types are specified, they are space-delimited within the attribute value.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Union**.  
  
 You can choose multiple simple data types in the drop-down list for this property by using the check boxes associated with each such data type.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)