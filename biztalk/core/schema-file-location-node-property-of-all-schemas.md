---
title: "Schema File Location (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schema File Location property [schemas]"
ms.assetid: aa6dec35-456b-4370-b8ee-30a3b28eb36e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema File Location (Node Property of All Schemas)
Use the **Schema File Location** property to examine the file system location of the schema file that contains the schema being edited.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 General  
  
## Read-Only Value  
 The file system location of the schema file that contains the schema being edited.  
  
## Default Value  
 By default schema files are given the name "Schema*N*.xsd", where "*N*" is a monotonically increasing value starting with one. Also, by default, they reside in the project folder associated with the project in which they are created.  
  
## XSD Persistence  
 This property is not persisted in the XSD itself, but is persisted as the name and file system location of the schema file, as well as in the BizTalk project file.  
  
## Remarks  
 You can examine this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)