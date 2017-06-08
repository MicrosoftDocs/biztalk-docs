---
title: "Block (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Block property [schemas]"
ms.assetid: 068c9913-183e-452d-a66f-9b0a12f259d9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Block (Node Property of All Schemas)
Use the **Block** property to prevent or restrict the types of derivations that can be used in instance messages for the element(s) corresponding to the selected **Record** node.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **block** attribute, if present, specifying that there are no restrictions on particular types of derivations unless otherwise specified by the [BlockDefault](../core/blockdefault-node-property-of-all-schemas.md) property.|  
|**All**|Sets the **block** attribute to "#all", specifying that no derivations are allowed.|  
|**Restriction**|Adds "restriction" to the value of the **block** attribute, specifying that derivations by restriction are not allowed.|  
|**Extension**|Adds "extension" to the value of the **block** attribute, specifying that derivations by extension are not allowed.|  
|**Substitution**|Adds "substitution" to the value of the **block** attribute, specifying that derivations by substitution are not allowed.|  
  
## Default Value  
 **(Default)**  
  
## XSD Persistence  
 As the value of the **block** attribute of the **complexType** element that is a child of the element that corresponds to the selected **Record** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 The values **Restriction**, **Extension**, and **Substitution** can be set in combination with each other by selecting their corresponding check boxes in the **Block** property drop-down list. The corresponding values of the **block** attribute are space-separated.  
  
 In corresponding instance messages, other derived data types can be used for a particular element unless explicitly prevented by the settings of the **Block** and/or **BlockDefault** properties, as follows:  
  
```  
<RecordName   
            xmlns:xsi="http://www.w3c.org/2001/XMLSchema-instance>"  
  
```  
  
 In the example above, "BaseOrDerivedTypeName" is the name of a complex type that is derived from the data type specified by the **Data Structure Type** property of the corresponding **Record** node by some allowed type of derivation (a type of derivation that is not blocked by this property or the **BlockDefault** property). For more information about different types of derivations, see [Type Reuse and Derivations](../core/type-reuse-and-derivations.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [BlockDefault (Node Property of All Schemas)](../core/blockdefault-node-property-of-all-schemas.md)