---
title: "FinalDefault (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FinalDefault property [schemas]"
ms.assetid: 6e5a6169-043c-4e6f-bf58-b5983f3f7650
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FinalDefault (Node Property of All Schemas)
Use the **FinalDefault** property to specify a global setting that restricts different types of derivations from the data types defined for **Record**, **Field Element**, or **Field Attribute** nodes within the schema being edited.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **finalDefault** attribute, if present, specifying that the default behavior should be provided.|  
|**All**|Sets the **finalDefault** attribute to "#all", preventing all derivations from the data types defined for all of the **Record**, **Field Element**, and **Field Attribute** nodes in the schema.|  
|**Restriction**|Adds "restriction" to the value of the **finalDefault** attribute, preventing derivations by restriction from the data types defined for all of the **Record**, **Field Element**, and **Field Attribute** nodes in the schema.|  
|**Extension**|Adds "extension" to the value of the **finalDefault** attribute, preventing derivations by extension from the data types defined for all of the **Record** nodes in the schema.|  
|**List**|Adds "list" to the value of the **finalDefault** attribute, preventing derivations using lists from the data types defined for all of the **Field Element** and **Field Attribute** nodes in the schema.|  
|||  
  
## Default Value  
 **(Default)**, specifying that there are no restrictions regarding how the data type defined for all of the **Record**, **Field Element**, and **Field Attribute** nodes in the schema can be inherited.  
  
## XSD Persistence  
 As the value of the **finalDefault** attribute of the **schema** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 The values **Restriction**, **Extension**, **List**, and **Union** can be set in combination with each other by selecting their corresponding check boxes in the **FinalDefault** property drop-down list. The corresponding values of the **finalDefault** attribute are space-separated.  
  
 You can override the global setting established by this property by setting the [Final](../core/final-node-property-of-all-schemas.md) property for individual **Record**, **Field Element**, and **Field Attribute** nodes.  
  
 For more information about different types of derivations, see [Type Reuse and Derivations](../core/type-reuse-and-derivations.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [Final (Node Property of All Schemas)](../core/final-node-property-of-all-schemas.md)