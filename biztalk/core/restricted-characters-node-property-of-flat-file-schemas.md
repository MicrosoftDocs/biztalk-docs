---
title: "Restricted Characters (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Restricted Characters property [Flat File schemas]"
ms.assetid: 854422a3-49c9-4a2e-81b2-f62e38886491
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restricted Characters (Node Property of Flat File Schemas)
Use the **Restricted Characters** property to define ranges of characters that are restricted in instance messages.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 A set of zero or more non-overlapping character ranges, as configured in the **Restricted Characters** dialog box.  
  
## Default Value  
 No restricted character ranges.  
  
## XSD Persistence  
 Each restricted character range is persisted as the values of the **start** and **end** attributes of a **schema/annotation/appinfo/schemaInfo/restrictedCharacterRanges/interval** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 Click the ellipsis (**...**) button located to the right of the value field for this property to open the **Restricted Characters** dialog box. In this dialog box, specify one or more ranges of restricted characters.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)