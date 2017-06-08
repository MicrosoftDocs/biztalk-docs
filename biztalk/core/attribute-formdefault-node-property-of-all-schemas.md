---
title: "Attribute FormDefault (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Attribute FormDefault property [schemas]"
ms.assetid: 46cfd564-b2d0-4d9a-ba11-0ccef79cf81f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Attribute FormDefault (Node Property of All Schemas)
Use the **Attribute FormDefault** property to define whether locally declared attributes must be qualified by using a namespace identifier throughout instance messages.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **attributeFormDefault** attribute, if present, specifying the default behavior corresponding to the "Unqualified" setting.|  
|**Qualified**|Sets the **attributeFormDefault** attribute to "qualified", specifying that locally declared attributes must be qualified by a namespace identifier throughout instance messages.|  
|**Unqualified**|Sets the **attributeFormDefault** attribute to "unqualified", specifying that locally declared attributes need not be qualified by a namespace identifier throughout instance messages.|  
  
## Default Value  
 **(Default)**, specifying default behavior corresponding to the "Unqualified" setting.  
  
## XSD Persistence  
 As the value of the **attributeFormDefault** attribute of the **schema** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 You can override the global setting established by this property by setting the [Form](../core/form-node-property-of-all-schemas.md) property for individual **Field Attribute** nodes.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [Form (Node Property of All Schemas)](../core/form-node-property-of-all-schemas.md)