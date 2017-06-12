---
title: "Filename (Schema Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, naming conventions"
  - "schemas, files"
  - "schema item properties, Filename property"
  - "Filename property [schema item]"
ms.assetid: f2185094-4476-4b4e-8ba5-7d5f4e9a797e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Filename (Schema Item Property)
Use the **Filename** property to examine and set the name of the selected schema file.  
  
## Category  
 Miscellaneous  
  
## Allowed Values  
 A valid, pathless file name with an .xsd extension.  
  
## Default Value  
 Schema*N*.xsd, where "*N*" is a monotonically increasing number.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a schema file in Solution Explorer.  
  
 This property stores the actual name of the schema file on your hard disk. If you change this property value within the context of the project, the file is renamed on the disk and the project will be updated to reference the renamed file.