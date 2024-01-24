---
description: "Learn more about: Error - Schema Root Reference Empty"
title: "Error - Schema Root Reference Empty"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.rootRefEmpty"
---
# Error - Schema Root Reference Empty
**Error Code**  
  
 BEC2005  
  
 **Explanation**  
  
 The **Root Reference** property of the **Schema** node is not set. When the **Standard** property of the **Schema** node is set to a value other than **XML**, you must set the **Root Reference** property to indicate which child node of the **Schema** node is meant to be used as the root of the message defined by this schema.  
  
 **User Action**  
  
 As appropriate for your schema, either set the **Standard** property of the **Schema** node to **XML**, or set the **Root Reference** property of the **Schema** node to the appropriate child node of the **Schema** node. These child nodes are the available in the **Root Reference** property drop-down list.
