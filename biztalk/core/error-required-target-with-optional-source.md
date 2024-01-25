---
description: "Learn more about: Error - Required Target with Optional Source"
title: "Error - Required Target with Optional Source"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.reqdTargetWithOptionalSource"
---
# Error - Required Target with Optional Source
**Error Code**  
  
 btm1001  
  
 **Explanation**  
  
 The data for the indicated required node in the destination schema comes from an optional node in the source schema. Therefore, there may be valid instance messages for which mapping will fail.  
  
 **User Action**  
  
 Confirm the optional and required characteristics of the specified source and destination nodes, respectively, and consider making these characteristics match.
