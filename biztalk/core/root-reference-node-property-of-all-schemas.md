---
title: "Root Reference (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Root Reference property [schemas]"
ms.assetid: 66ec55e0-e634-4ce0-8eb8-711b638f6272
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Root Reference (Node Property of All Schemas)
Use the **Root Reference** property to specify the node that represents the outermost element in the XML business document represented by the schema.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Removes the **root_reference** attribute, if present, resulting in classes being generated for all root nodes when the schema is compiled.|  
|Node names of all root **Record** nodes in the schema.|The other available values are the names (**Node Name** property value) of the root **Record** nodes currently defined in the schema.|  
  
## Default Value  
 **(Default)**, resulting in classes being generated for all root nodes when the schema is compiled.  
  
## XSD Persistence  
 As the value of the **root_reference** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 Any root **Record** node in your schema can be configured as the value for the **Root Reference** property.  
  
 BizTalk Mapper uses this property to determine which root node and substructure to use in the map if a schema has multiple root nodes. If it is not set, BizTalk Mapper will prompt for the appropriate root node to use for mapping.  
  
 If you configure this property, use the schema to develop a map, and then later change the value of this property, the map will not automatically update to use the new root reference.  
  
 If the **Root Reference** property is not set, .NET classes will be generated for each and every root **Record** node (direct child nodes of the **Schema** node) during the BizTalk project build process (also known as schema compilation). You should avoid this scenario when you have a large number of such root nodes defined in your schema because so many .NET classes will be generated in the resulting BizTalk assembly and ultimately deployed to the database. If a particular root node is always going to be used for instance validation and so on, you should set it as the value of the **Root Reference** property, resulting in a single .NET class being generated for the schema.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)