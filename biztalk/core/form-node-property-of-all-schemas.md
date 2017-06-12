---
title: "Form (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Form property [schemas]"
ms.assetid: f111b9cd-8343-457f-9c90-1dc96b2463eb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Form (Node Property of All Schemas)
Use the **Form** property to define whether local elements and attributes in instance messages must be qualified with a namespace identifier.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **form** attribute, if present, specifying the default behavior, which corresponds to the **Unqualified** setting.|  
|**Qualified**|Sets the **form** attribute to "qualified", specifying that locally declared elements must be qualified by a namespace identifier in instance messages.|  
|**Unqualified**|Sets the **form** attribute to "unqualified", specifying that locally declared elements need not be qualified by a namespace identifier in instance messages.|  
  
## Default Value  
 **(Default)**, specifying the default behavior corresponding to the **Unqualified** setting.  
  
## XSD Persistence  
 As the **form** (="qualified" or "unqualified") attribute of the **element** or **attribute** element that corresponds to the selected **Record**, **Field Element**, or **Field Attribute**, respectively.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record**, **Field Element**, or **Field Attribute** node in BizTalk Editor.  
  
 This property provides the ability to specify the requirements for namespace qualification on a node-by-node basis.  
  
 For **Record** and **Field Element** nodes, the **Form** property overrides the setting of the [Element FormDefault](../core/element-formdefault-node-property-of-all-schemas.md) property of the **Schema** node.  
  
 For **Field Attribute** nodes, the **Form** property overrides the setting of the [Attribute FormDefault](../core/attribute-formdefault-node-property-of-all-schemas.md) property of the **Schema** node.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)