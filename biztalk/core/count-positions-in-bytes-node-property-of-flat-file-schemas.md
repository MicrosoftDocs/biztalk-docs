---
title: "Count Positions In Bytes (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Count Positions In Bytes property [Flat File schemas]"
ms.assetid: 56eccdab-d4fb-4f8b-b39d-b269929b30c2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Count Positions In Bytes (Node Property of Flat File Schemas)
Use the **Count Positions In Bytes** property to configure whether the positions will be counted in bytes rather than characters.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Yes**|Sets the **count_positions_by_bytes** attribute to "true", specifying that position counting should be done by bytes.|  
|**No**|Sets the **count_positions_by_bytes** attribute to "false", specifying that position counting should be done by characters.|  
  
## Default Value  
 **No**  
  
## XSD Persistence  
 As the value of the **count_positions_by_bytes** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)