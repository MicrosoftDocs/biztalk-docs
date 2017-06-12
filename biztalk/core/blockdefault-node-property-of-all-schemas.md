---
title: "BlockDefault (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BlockDefault property [schemas]"
ms.assetid: 86e41518-e11b-4d56-8894-c33ae8f4f9f2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BlockDefault (Node Property of All Schemas)
Use the **BlockDefault** property to prevent or restrict the types of derivations that can be used in instance messages for all data types defined by the schema being edited.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **blockDefault** attribute, if present, specifying that there are no restrictions on particular types of derivations that apply throughout the entire schema.|  
|**All**|Sets the **blockDefault** attribute to "#all", specifying that no derivations are allowed.|  
|**Restriction**|Adds "restriction" to the value of the **blockDefault** attribute, specifying that derivations by restriction are not allowed.|  
|**Extension**|Adds "extension" to the value of the **blockDefault** attribute, specifying that derivations by extension are not allowed.|  
|**Substitution**|Adds "substitution" to the value of the **blockDefault** attribute, specifying that derivations by substitution are not allowed.|  
  
## Default Value  
 **(Default)**, resulting in no global restrictions on deriving from the types in the schema being edited.  
  
## XSD Persistence  
 As the value of the **blockDefault** attribute of the **schema** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 The values **Restriction**, **Extension**, and **Substitution** can be set in combination with each other by selecting their corresponding check boxes in the **BlockDefault** property drop-down list. The corresponding values of the **blockDefault** attribute are space-separated.  
  
 You can override the global setting established by this property by setting the [Block](../core/block-node-property-of-all-schemas.md) property of individual **Record** nodes.  
  
 In corresponding instance messages, other derived data types can be used for a particular element unless explicitly prevented by the settings of the **Block** and/or **BlockDefault** properties, as follows:  
  
```  
<RecordName   
            xmlns:xsi="http://www.w3c.org/2001/XMLSchema-instance>"  
  
```  
  
 In the example above, "BaseOrDerivedTypeName" is the name of a complex type that is derived from the data type specified by the **Data Structure Type** property of the corresponding **Record** node by some allowed type of derivation (a type of derivation that is not blocked by this property or the **BlockDefault** property). For more information about different types of derivations, see [Type Reuse and Derivations](../core/type-reuse-and-derivations.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)