---
title: "Source Schema (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Schema property [grid pages]"
ms.assetid: 8b813b34-2322-4dbb-b906-6a300999dcde
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Source Schema (Grid Property)
Use the **Source Schema**  property to view the chosen source schema.  
  
## Category  
 General  
  
## Allowed Values  
  
|Value|Description|  
|-----------|-----------------|  
|Relative path to the source schema file|Most often, the relative path is ".\\", indicating that the source schema file resides in the project folder, along with the map file itself.|  
|**Fully Qualified Name** property value|When the source schema is from another BizTalk project (another assembly), the value of the **Fully Qualified Name** property of the source schema is stored in this property.|  
|**Inline**|Specifies that the source schema for this map is a multipart schema from Orchestration Designer.|  
  
## Default Value  
 **Inline**  
  
## Remarks  
 Normally, BizTalk Mapper stores references to the source schema in the map file (.btm file) as a filepath (source schema files) or Fully Qualified Name (source schemas within assemblies). When the value of this property is set to **Inline**, the source schema is a multipart schema from Orchestration Designer. Such schemas are thin wrappers, stored within the map file, that internally refer to the various partial schemas that make up the complete, if virtual, source schema used to design the data mapping.  
  
> [!NOTE]
>  You cannot edit the **Source Schema**  property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)