---
title: "Enumeration (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Enumeration property [schemas]"
ms.assetid: 7c99c5fe-cfd9-4669-af24-e4825d8e91ae
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enumeration (Node Property of All Schemas)
Use the **Enumeration** property to limit any data in an instance message corresponding to the selected **Field Element** or **Field Attribute** node to a specific set of values.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
 A set of strings, each on its own line, as specified in the **Enumeration Editor** dialog box.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of an **enumeration** element for each string provided using the **Enumeration Editor** dialog box with their **value** attributes set to the individual strings.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived Type** property to **Restriction**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 Click the ellipsis (**...**) button located to the right of the value field for this property to open the **Enumeration Editor** dialog box in which you can provide a set of strings for the enumeration, one per line.  
  
 For a given **Field Element** or **Field Attribute** node, do not use both the **Enumeration** property and the **CodeList** property. Using the latter property can result in values entered using the former property to be overwritten.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)