---
title: "MaxFacet Value (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MaxFacet Value property [schemas]"
ms.assetid: 5d3f9ab4-4f52-41f6-8ef0-baa3bf9ad97f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MaxFacet Value (Node Property of All Schemas)
Use the **MaxFacet Value** property to specify the maximum value (inclusive or exclusive, as specified by the **MaxFacet Type** property) for any instance message data corresponding to the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
 Either:  
  
-   No value, specifying that there is no maximum value for this ordered data type. This will also change the **MaxFacet Type** property back to **(Default)**.  
  
-   Any manually entered value that is compatible with the specified base data type.  
  
## Default Value  
 No value, specifying that there is no maximum value for this ordered data type.  
  
## XSD Persistence  
 As the value of the **value** attribute of either the **maxExclusive** or **maxInclusive** element within the **restriction** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to ordered base data types, such as "xs:integer".  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)