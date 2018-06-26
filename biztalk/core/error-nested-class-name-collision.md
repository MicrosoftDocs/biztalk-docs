---
title: "Error - Nested Class Name Collision | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.nestedClassNameCollision"
ms.assetid: dd636d25-d0c1-41be-a2ba-b38ea97b973d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Nested Class Name Collision
**Error Code**  

 BEC2017  

 **Explanation**  

 The **Type Name** property of this schema was found to be the same as the **RootNode TypeName** property of one of the root nodes in the schema. C# disallows nested classes with the same names; therefore this condition causes an error.  

 **User Action**  

 You must change one or both of the relevant property values so that you avoid the name collision. Either:  

- Select the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Type Name** property to a unique valid value.  

   \- or -  

- Select the indicated root node, and then in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change the **RootNode TypeName** property to a unique valid value.
