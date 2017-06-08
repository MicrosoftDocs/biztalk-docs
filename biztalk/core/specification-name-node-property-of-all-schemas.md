---
title: "Specification Name (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Specification Name property [schemas]"
ms.assetid: 4260e1df-d6a4-49d0-a5ae-321f59e78f89
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Specification Name (Node Property of All Schemas)
Use the **Specification Name** property to designate a business name for the schema.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
 Any string allowed in XML.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **schema_name** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Schema** node in BizTalk Editor.  
  
 An example of setting this property is when you are creating a purchase order that you use exclusively with your supply chain management process, you might enter a value of "Supply Change PO" for this property.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)