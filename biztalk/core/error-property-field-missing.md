---
title: "Error - Property Field Missing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.propFieldMissing"
ms.assetid: 8d07e72b-f876-4a37-8c95-ec7aa0033983
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Property Field Missing
**Error Code**  
  
 BEC2008  
  
 **Explanation**  
  
 The indicated node in this schema is being promoted to a **Field Element** node in the corresponding property schema that does not exist. This condition can occur when a **Field Element** node is removed from, or renamed in, a property schema after it has been used as the target of a property promotion.  
  
 **User Action**  
  
 Either modify the property schema so that it contains the missing **Field Element** node, or use the **Promote Properties** dialog box to delete or otherwise modify the relevant property promotion.