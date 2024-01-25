---
description: "Learn more about: Error - Property Field Missing"
title: "Error - Property Field Missing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.propFieldMissing"
---
# Error - Property Field Missing
**Error Code**  
  
 BEC2008  
  
 **Explanation**  
  
 The indicated node in this schema is being promoted to a **Field Element** node in the corresponding property schema that does not exist. This condition can occur when a **Field Element** node is removed from, or renamed in, a property schema after it has been used as the target of a property promotion.  
  
 **User Action**  
  
 Either modify the property schema so that it contains the missing **Field Element** node, or use the **Promote Properties** dialog box to delete or otherwise modify the relevant property promotion.
