---
title: "Tag Identifier (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tag Identifier property [schemas], about Tag Identifier property"
  - "Tag Identifier property [schemas]"
ms.assetid: 3e37e433-e69c-47ce-b257-190cac7b80ae
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tag Identifier (Node Property of Flat File Schemas)
Use the **Tag Identifier** property to specify an identifying tag for a non-XML record.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Any string that is valid in XML.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **tag_name** attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Tag Offset (Node Property of Flat File Schemas)](../core/tag-offset-node-property-of-flat-file-schemas.md)