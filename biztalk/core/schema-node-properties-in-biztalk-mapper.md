---
title: "Schema Node Properties in BizTalk Mapper | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema node properties, BizTalk Mapper"
  - "schema node properties, editing"
  - "schema node properties, viewing"
ms.assetid: 15cd7271-c9cb-42b1-8f2b-62fe5efdd497
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Node Properties in BizTalk Mapper
You can view but not change the values of node properties in the source and destination schemas in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. If you need to change a schema node property value, you must open the schema in BizTalk Editor, change the appropriate property values, and then save the schema. You can then view the changed properties the next time you open the map that contains the schema in BizTalk Mapper.  
  
 The one exception to this rule is a schema node property that is only available for editing and viewing within BizTalk Mapper. If, in BizTalk Mapper, you select a **Record** node (with its **Mixed** property set to **True**), **Field Element** node, or **Field Attribute** node, the **Value** property can be set and subsequently examined.  
  
 The following table describes the source and destination schema node property that can be set from within BizTalk Mapper.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Value](../core/value-schema-node-property.md)|General|Specifies a default value for the selected node for use during transformation.|