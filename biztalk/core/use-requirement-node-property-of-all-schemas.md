---
title: "Use Requirement (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Use Requirement property [schemas]"
ms.assetid: 4719dab3-a493-4bef-a0e3-1f78de51de95
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use Requirement (Node Property of All Schemas)
Use the **Use Requirement** property to specify whether the selected **Field Attribute** node is required in an instance message.  
  
## Applies to Nodes of Type  
 [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **use** attribute, if present, which is equivalent to specifying that the attribute corresponding to the selected **Field Attribute** node is optional in instance messages (same as **Optional**).|  
|**Optional**|Sets the **use** attribute to "optional", specifying that the attribute corresponding to the selected **Field Attribute** node is optional in conforming instance messages.|  
|**Prohibited**|Sets the **use** attribute to "prohibited", specifying that the attribute corresponding to the selected **Field Attribute** node is not allowed in conforming instance messages. **Field Attribute** nodes can only be prohibited within larger structures that are being reused through derivation.|  
|**Required**|Sets the **use** attribute to "required", specifying that the attribute corresponding to the selected **Field Attribute** node is required in conforming instance messages. You cannot set values for the **Default** and **Fixed** properties when this property is set to **Required**.|  
  
## Default Value  
 **(Default)**, which means that **use** attribute is not present, providing the default XSD behavior of the attribute corresponding to the selected **Field Attribute** node being optional in instance messages.  
  
## XSD Persistence  
 As the value of the **use** attribute (="optional", "prohibited", or "required") of the **attribute** element corresponding to the selected **Field Attribute** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Attribute** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)