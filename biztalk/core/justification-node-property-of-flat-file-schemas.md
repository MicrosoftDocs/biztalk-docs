---
title: "Justification (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Justification property [Flat File schemas]"
ms.assetid: d26646dc-71d1-45b9-a162-82d36eeb4008
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Justification (Node Property of Flat File Schemas)
Use the **Justification** property to configure the justification of **Field Element** and **Field Attribute** node contents, which is used by the non-XML parsers.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Left**|Use this value if the instance message data corresponding to the selected **Field Element** or **Field Attribute** node is left-justified.|  
|**Right**|Use this value if the instance message data corresponding to the selected **Field Element** or **Field Attribute** node is right-justified.|  
  
## Default Value  
 **Left**  
  
## XSD Persistence  
 As the value of the **justification** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)