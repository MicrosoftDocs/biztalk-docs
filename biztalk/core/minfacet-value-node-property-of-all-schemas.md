---
title: "MinFacet Value (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MinFacet Value property [schemas], about MinFacet Value property"
  - "MinFacet Value property [schemas]"
ms.assetid: 08d59136-21f5-464d-89e9-e93fab08d23b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MinFacet Value (Node Property of All Schemas)
Use the **MinFacet Value** property to configure the minimum value (inclusive or exclusive, as specified by the **MinFacet Type** property) for any instance message data corresponding to the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
 Either:  
  
-   No value, specifying that there is no minimum value for this ordered data type. This will also change the **MinFacet Type** property back to **(Default)**.  
  
-   Any manually entered value that is compatible with the specified base data type.  
  
## Default Value  
 No value, specifying that there is no minimum value for this ordered data type.  
  
## XSD Persistence  
 As the value of the **value** attribute of either the **minExclusive** or **minInclusive** element within the **restriction** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to ordered base data types, such as "xs:integer".  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)