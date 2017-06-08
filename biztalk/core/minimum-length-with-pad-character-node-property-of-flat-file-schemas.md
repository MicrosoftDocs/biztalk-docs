---
title: "Minimum Length with Pad Character (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Minimum Length with Pad Character property [Flat File schemas], about Minimum Length with Pad Character property"
  - "Minimum Length with Pad Character property [Flat File schemas]"
ms.assetid: 0a2dbfb2-4956-44f1-a67c-56ef1e7ad29c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Minimum Length with Pad Character (Node Property of Flat File Schemas)
Use the **Minimum Length with Pad Character** property to configure how a serializer pads the instance message data associated with the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 No value, resulting in no annotation being added to the XSD representation of the schema and no padding being performed, or a positive integer indicating the minimum length to which the field associated with the selected **Field Element** or **Field Attribute** node should be padded.  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema and no padding being performed.  
  
## XSD Persistence  
 As the value of the **min_length_with_pad** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the containing **Record** node to **Delimited**  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)