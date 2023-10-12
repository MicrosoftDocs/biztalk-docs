---
description: "Learn more about: Error - Promoted Property Max Occurs"
title: "Error - Promoted Property Max Occurs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.promoPropMaxOccurs"
---
# Error - Promoted Property Max Occurs
**Error Code**  
  
 BEC2002  
  
 **Explanation**  
  
 The setting of the **Max Occurs** property of the node being promoted, or of one of its ancestor nodes, is incompatible with property promotion. Property promotion is disallowed for nodes that can occur more than once in an instance message. Therefore, the **Max Occurs** properties of all nodes from the node being promoted back to the root node must be set to 1.  
  
 **User Action**  
  
 Ensure that the **Max Occurs** property of the node being promoted and all of its ancestor nodes is set to one (1).
