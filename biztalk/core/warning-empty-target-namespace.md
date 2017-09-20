---
title: "Warning - Empty Target Namespace | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.emptyTargetNamespace"
ms.assetid: 00d43bcc-6fd6-4766-b91d-f6c33608c6c1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Warning - Empty Target Namespace
**Error Code**  
  
 BEC1007  
  
 **Explanation**  
  
 The **Target Namespace** property of the **Schema** node has not been set. Although not required, it is recommended that you define a unique target namespace for each of your schemas.  
  
 **User Action**  
  
 Unless there is a good reason not to, select the **Schema** node of this schema, and then in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, provide a value for the **Target Namespace** property that is unique to this schema.