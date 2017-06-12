---
title: "Target Schema (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Target Schema property [grid pages]"
ms.assetid: cb07dd68-e0cb-4b69-94ba-e90d6437cda8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Target Schema (Grid Property)
Use the **Target Schema** property to view the chosen destination schema.  
  
## Category  
 General  
  
## Allowed Values  
  
|Value|Description|  
|-----------|-----------------|  
|Relative path to the destination schema file|Most often, the relative path is ".\\", indicating that the destination schema file resides in the project folder, along with the map file itself.|  
|**Fully Qualified Name** property value|When the destination schema is from another BizTalk project (another assembly), the value of the **Fully Qualified Name** property of the destination schema is stored in this property.|  
|**Inline**|Specifies that the destination schema for this map is a multipart schema from Orchestration Designer.|  
  
## Default Value  
 **Inline**  
  
## Remarks  
 Normally, BizTalk Mapper stores references to the destination schema in the map file (.btm file) as a filepath (schema files) or Fully Qualified Name (schemas within assemblies). When the value of this property is set to **Inline**, the destination schema is a multipart schema from Orchestration Designer. Such schemas are thin wrappers, stored within the map file, that internally refer to the various partial schemas that make up the complete, if virtual, destination schema used to design the data mapping.  
  
> [!NOTE]
>  You cannot edit the **Target Schema**  property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)