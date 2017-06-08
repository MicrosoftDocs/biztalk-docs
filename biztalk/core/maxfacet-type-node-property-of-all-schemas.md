---
title: "MaxFacet Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MaxFacet Type property [schemas]"
ms.assetid: 03718aa0-e392-41fc-a389-405a2d092f73
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MaxFacet Type (Node Property of All Schemas)
Use the **MaxFacet Type** property to define whether the upper bound of any instance message value corresponding to the selected **Field Element** or **Field Attribute** node, as specified by the **MaxFacet Value** property, is inclusive or exclusive.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Exclusive**|Adds the **maxExclusive** element as a subelement of the **restriction** element, specifying that the maximum value of any data associated with the selected **Field Element** or **Field Attribute** node excludes the value specified by the **MaxFacet Value** property.|  
|**Inclusive**|Adds the **maxInclusive** element as a subelement of the **restriction** element, specifying that the maximum value of any data associated with the selected **Field Element** or **Field Attribute** node includes the value specified by the **MaxFacet Value** property.|  
|**(Default)**|Removes any **maxExclusive** or **maxInclusive** element from the **restriction** element, specifying that there is no maximum value for any data associated with the selected **Field Element** or **Field Attribute** node. Also removes any value specified for the **MaxFacet Value** property.|  
  
## Default Value  
 **(Default)**, resulting in no **maxExclusive** or **maxInclusive** element within the **restriction** element and specifying that there is no maximum value for any data associated with the selected **Field Element** or **Field Attribute** node.  
  
## XSD Persistence  
 As a **maxExclusive** or **maxInclusive** element within the **restriction** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**. Further, the **MaxFacet Type** property cannot be set until a value is entered for the **MaxFacet Value** property. Then the **MaxFacet Type** property defaults to **Inclusive**, but can be changed to **Exclusive**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to ordered base data types, such as "xs:integer".  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)