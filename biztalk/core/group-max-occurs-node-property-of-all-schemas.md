---
title: "Group Max Occurs (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Group Max Occurs property [schemas]"
ms.assetid: 17318b5b-29b9-42d7-88af-b2a742cf3f60
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Group Max Occurs (Node Property of All Schemas)
Use the **Group Max Occurs** property to specify the maximum number of times the underlying group content of the selected **Record** node can occur in a given scope in an instance message.  
  
> [!NOTE]
>  If an ancestor node can occur multiple times, the total occurrences of the selected **Record** node can be greater than the occurrence range specified by the values of the [Group Min Occurs](../core/group-min-occurs-node-property-of-all-schemas.md) property and this property.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Edit box value|Description|  
|--------------------|-----------------|  
|Non-negative integer|Any value greater than one (1) will enable the underlying content that corresponds to the selected **Record** node to occur multiple times in an instance message. If you do not want the underlying content to occur more than once, set the value of this property to one (1), or leave it blank. To prevent all occurrences, set the value of this property to zero (0).|  
|"unbounded"<br /><br /> "*"|Use this value if you do not know how many loops you might have in an instance message and you do not want to lose any data. An asterisk ("*") is a valid abbreviation for the literal string value "unbounded".|  
|No value|Use this property value to restore the behavior to the default value of one (1).|  
  
## Default Value  
 No value, resulting in the default behavior corresponding to a value of one (1).  
  
## XSD Persistence  
 As the value of the **maxOccurs** attribute of the **sequence**, **choice**, or **all** element within the element that corresponds to the selected **Record** node.  
  
> [!NOTE]
>  The literal string "unbounded", and not an asterisk (*), is persisted in the XSD.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.  
  
 Configure this property only for **Record** nodes that have underlying group content.  
  
 The value of this property should always be greater than or equal to the value of the **Group Min Occurs** property.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)