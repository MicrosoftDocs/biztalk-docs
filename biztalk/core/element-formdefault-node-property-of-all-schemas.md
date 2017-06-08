---
title: "Element FormDefault (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Element FormDefault property [schemas]"
ms.assetid: 80e0ff7d-38cb-49dc-9044-1a2547752f63
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Element FormDefault (Node Property of All Schemas)
Use the **Element FormDefault** property to define whether locally declared elements must be qualified by using a namespace identifier throughout instance messages.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **elementFormDefault** attribute, if present, specifying the default behavior, which corresponds to the "Unqualified" setting.|  
|**Qualified**|Sets the **elementFormDefault** attribute to "qualified", specifying that locally declared elements must be qualified by a namespace identifier throughout instance messages.|  
|**Unqualified**|Sets the **elementFormDefault** attribute to "unqualified", specifying that locally declared elements need not be qualified by a namespace identifier throughout instance messages.|  
  
## Default Value  
 **(Default)**, specifying the default behavior, which corresponds to the "Unqualified" setting.  
  
## XSD Persistence  
 As the value of the **elementFormDefault** attribute of the **schema** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 You can override the global setting established by this property by setting the [Form](../core/form-node-property-of-all-schemas.md) property for individual **Record** and **Field Element** nodes.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [Form (Node Property of All Schemas)](../core/form-node-property-of-all-schemas.md)