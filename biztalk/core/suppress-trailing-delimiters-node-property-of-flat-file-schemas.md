---
title: "Suppress Trailing Delimiters (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Suppress Trailing Delimiter property [schemas]"
ms.assetid: ec30cc12-a074-4077-9665-17825d7af738
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Suppress Trailing Delimiters (Node Property of Flat File Schemas)
Use the **Suppress Trailing Delimiter** property to suppress trailing delimiters associated with the selected **Record** node.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Yes**|Use this value to suppress trailing delimiters in instance messages.|  
|**No**|Use this value to include trailing delimiters in instance messages.|  
  
## Default Value  
 **No**  
  
## XSD Persistence  
 As the value of the **suppress_trailing_delimiters** (="true" or "false") attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the selected **Record** node to **Delimited**  
  
 When an element is entirely missing from an instance message, such as when it is optional, the corresponding delimiter will always be missing, regardless of the setting of this property.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)