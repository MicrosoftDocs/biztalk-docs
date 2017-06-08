---
title: "MinFacet Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MinFacet Type property [schemas]"
  - "MinFacet Type property [schemas], about MinFacet Type property"
ms.assetid: 29a479f7-2b79-4c39-bbee-7e4293994c1b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MinFacet Type (Node Property of All Schemas)
Use the **MinFacet Type** property to define whether the lower bound of any instance message value corresponding to the selected **Field Element** or **Field Attribute** node, as specified by the **MinFacet Value** property, is inclusive or exclusive.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Exclusive**|Adds the **minExclusive** element as a subelement of the **restriction** element, specifying that the minimum value of any data associated with the selected **Field Element** or **Field Attribute** node excludes the value specified by the **MinFacet Value** property.|  
|**Inclusive**|Adds the **minInclusive** element as a subelement of the **restriction** element, specifying that the minimum value of any data associated with the selected **Field Element** or **Field Attribute** node includes the value specified by the **MinFacet Value** property.|  
|**(Default)**|Removes any **minExclusive** or **minInclusive** element from the **restriction** element, specifying that there is no minimum value for any data associated with the selected **Field Element** or **Field Attribute** node. Also removes any value specified for the **MinFacet Value** property.|  
  
## Default Value  
 **(Default)**, resulting in no **minExclusive** or **minInclusive** element within the **restriction** element and specifying that there is no minimum value for any data associated with the selected **Field Element** or **Field Attribute** node.  
  
## XSD Persistence  
 As a **minExclusive** or **minInclusive** element within the **restriction** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived Type** property to **Restriction**. Further, you cannot set the **MinFacet Type** property until a value is entered for the **MinFacet Value** property. Then the **MinFacet Type** property defaults to **Inclusive**, but you can change it to **Exclusive**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to ordered base data types, such as "xs:integer".  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)