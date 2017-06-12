---
title: "Group Min Occurs (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Group Min Occurs property [schemas]"
ms.assetid: 462d442d-2a16-4c57-9f4e-b6330f827acb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Group Min Occurs (Node Property of All Schemas)
Use the **Group Min Occurs** property to specify the minimum number of times the underlying group content of the selected **Record** node can occur in a given scope in an instance message.  
  
> [!NOTE]
>  If an ancestor node can occur multiple times, the total occurrences of the selected **Record** node can be greater than the occurrence range specified by the values of this property and the [Group Max Occurs](../core/group-max-occurs-node-property-of-all-schemas.md) property.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Edit box value|Description|  
|--------------------|-----------------|  
|Positive integer|Any value greater than or equal to one (1), but required to be less than the value set for the [Group Max Occurs](../core/group-max-occurs-node-property-of-all-schemas.md) property.|  
|Zero (0)|Use this value if the underlying group content corresponding to the selected **Record** node need not even occur once in instance messages.|  
|No value|Use this property value to restore the behavior to the default value of one (1).|  
  
## Default Value  
 No value, resulting in the default behavior corresponding to a value of one (1).  
  
## XSD Persistence  
 As the value of the **minOccurs** attribute of the **sequence**, **choice**, or **all** element within the element that corresponds to the selected **Record** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.  
  
 Configure this property only for **Record** nodes that have underlying group content.  
  
 The value of this property should always be less than or equal to the value of the **Group Max Occurs** property.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)