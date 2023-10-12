---
description: "Learn more about: Error - Schema File Not In Build"
title: "Error - Schema File Not In Build"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.schemaFileNotInBuild"
---
# Error - Schema File Not In Build
**Explanation**  
  
 The command (**Validate Instance**, **Generate Instance**, or **Validate Schema**) could not be performed because the **Build Action** property of the schema file is set to **None**, preventing this schema from participating in these commands.  
  
 **User Action**  
  
 Select the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Build Action** property to a **Compile**. Then attempt the **Validate Instance**, **Generate Instance**, or **Validate Schema** command again.
