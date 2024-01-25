---
description: "Learn more about: Error - Could Generate Multiple Equivalent Children"
title: "Error - Could Generate Multiple Equivalent Children"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.couldGenMultipleEquivChildren"
---
# Error - Could Generate Multiple Equivalent Children
**Error Code**  
  
 btm1026  
  
 **Explanation**  
  
 Links to the destination schema inappropriately enable multiple nodes within an **Equivalent** group node to be generated.  
  
 **User Action**  
  
 Rework the links into the destination schema, potentially using logical functoids, so that only a single node within the **Equivalent** group node can be generated during mapping.
