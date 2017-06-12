---
title: "Structure (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Structure property [Flat File schemas]"
ms.assetid: db8bc83f-cb46-47b1-95ac-cebb57ae776c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Structure (Node Property of Flat File Schemas)
Use the **Structure** property to configure whether this non-XML record is positional or delimited.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Delimited**|Indicates that instance data corresponding to the currently selected record is delimited.|  
|**Positional**|Indicates that instance data corresponding to the currently selected record is positional.|  
  
## Default Value  
 **Delimited**, indicating that instance data corresponding to the currently selected record is delimited.  
  
## XSD Persistence  
 As the value of the **structure** (="delimited" or "positional") attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
 The setting of this property plays a major role in determining which other properties are available (visible).  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)