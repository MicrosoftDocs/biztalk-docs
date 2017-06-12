---
title: "CodeList Database (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeList Database property [schemas]"
ms.assetid: 424ee8f0-a870-4d7a-95fb-0432089ad9a8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CodeList Database (Node Property of All Schemas)
Use the **CodeList Database** property to specify the full path of the Microsoft Access database used for code lists. This database allows for easier configuration of enumerations associated with type derivations by restriction, especially when the enumeration choices are in the form of codes that are not particularly intuitive.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 BizTalk  
  
## Allowed Values  
 Legal, full path file names that identify Microsoft Access database files.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **codelist_database** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
> [!NOTE]
>  The **CodeList** and **CodeList Database** properties are used at design time only and are persisted in the XSD as corresponding settings for the **Enumeration** property. At run time, all values are verified against the **Enumeration** property only.  
  
 To make use of the appropriate database table in the Access database identified by this property, you must use the **CodeList** property associated with **Field Element** and **Field Attribute** nodes.  
  
 For conceptual information about working with code lists in BizTalk Editor, see [Code List Management](../core/code-list-management.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)