---
title: "Nillable (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Nillable property [schemas]"
ms.assetid: ca6f2282-de14-45cf-8672-191df723fd97
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Nillable (Node Property of All Schemas)
Use the **Nillable** property to specify whether the **nil** attribute can be used with the corresponding instance message element to indicate that it is still valid even if it has no content.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**True**|Sets the **nillable** attribute of the corresponding instance message element to "true", specifying that if the corresponding element in instance messages has a **nil** attribute with a value of "true", that element must not contain any data.|  
|**False**|Removes the **nillable** attribute of the corresponding instance message element, specifying that the **nil** attribute must not be used with the corresponding element in an instance message.|  
  
## Default Value  
 **False**, specifying that the **nil** attribute should not be used with the corresponding element or attribute in an instance message.  
  
## XSD Persistence  
 As the value of the **nillable** attribute of the element that corresponds to the selected **Record** or **Field Element** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** (including a root **Record** node) or **Field Element** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 In instance messages, the use of the **nil** attribute must include the namespace prefix for the XML Schema namespace for instances, http://www.w3.org/2001/xmlschema-instance, which is "xsi" by convention. An element in an instance message that includes the attribute setting **xsi:nil="true"** may not have any element content but it may still have attributes.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)