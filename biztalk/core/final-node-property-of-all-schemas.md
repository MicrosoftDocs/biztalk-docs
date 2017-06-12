---
title: "Final (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Final property [schemas]"
ms.assetid: dfbfd5b8-a9dc-404d-aa9a-6fad259bd319
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Final (Node Property of All Schemas)
Use the **Final** property to specify settings that will restrict different types of derivations from the data type defined for the selected **Record**, **Field Element**, or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 General Category for Record  
  
 Advanced Category for Element and Attribute  
  
## Allowed Values  
 The following table shows the values that can be set for this property when a **Record** node is selected in BizTalk Editor.  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **final** attribute, if present, specifying that there are no restrictions regarding how the data type defined for the selected **Record** node can be derived.|  
|**All**|Sets the **final** attribute to "#all", preventing all derivations from the data type defined for the selected **Record** node.|  
|**Restriction**|Adds "restriction" to the value of the **final** attribute, preventing derivations by restriction from the data type defined for the selected **Record** node.|  
|**Extension**|Adds "extension" to the value of the **final** attribute, preventing derivations by extension from the data type defined for the selected **Record** node.|  
  
 The following table shows the values that can be set for this property when a **Field Element** or **Field Attribute** node is selected in BizTalk Editor.  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **final** attribute, if present, specifying that there are no restrictions regarding how the data type defined for the selected **Field Element** or **Field Attribute** node can be derived.|  
|**All**|Sets the **final** attribute to "#all", preventing all derivations from the data type defined for the selected **Field Element** or **Field Attribute** node.|  
|**Restriction**|Adds "restriction" to the value of the **final** attribute, preventing derivations by restriction from the data type defined for the selected **Field Element** or **Field Attribute** node.|  
|**List**|Adds "list" to the value of the **final** attribute, preventing new data types from being derived using lists from the data type defined for the selected **Field Element** or **Field Attribute** node.|  
|**Union**|Adds "union" to the value of the **final** attribute, preventing new data types from being derived using unions from the data type defined for the selected **Field Element** or **Field Attribute** node.|  
  
## Default Value  
 **(Default)**, specifying that there are no restrictions regarding how the data type defined for the selected **Record**, **Field Element**,or **Field Attribute** node can be inherited.  
  
## XSD Persistence  
 For **Record** nodes, as a **final** attribute of the **complexType** element that corresponds to the selected **Record** node, set to either "#all" or some combination of the strings "extension" and "restriction".  
  
 For **Field Element** and **Field Attribute** nodes, as a **final** attribute of the **simpleType** element that corresponds to the selected **Field Element** and **Field Attribute** node, set to either "#all" or some combination of the strings "list", "restriction", and "union".  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** (including a root **Record** node), **Field Element**, or **Field Attribute** node in BizTalk Editor.  
  
 When you configure this property, you can prevent all derivations, or restrict, extend, or set the default derivation from a base type.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 For **Record** nodes, the values **Restriction** and **Extension** can be set in combination with each other by selecting their corresponding check boxes in the **Final** property drop-down list. The corresponding values of the **final** attribute are space-separated.  
  
 For **Field Element** and **Field Attribute** nodes, the values **Restriction**, **List**, and **Union** can be set in combination with each other by selecting their corresponding check boxes in the **Final** property drop-down list. The corresponding values of the **final** attribute are space-separated.  
  
 For more information about different types of derivations, see [Type Reuse and Derivations](../core/type-reuse-and-derivations.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [FinalDefault (Node Property of All Schemas)](../core/finaldefault-node-property-of-all-schemas.md)