---
description: "Learn more about: Error - Required Target Has Choice Node Source"
title: "Error - Required Target Has Choice Node Source"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.reqdTargetHasChoiceNodeSource"
---
# Error - Required Target Has Choice Node Source
**Error Code**  
  
 btm1029  
  
 **Explanation**  
  
 The indicated node in the destination schema is specified as required but is linked to a node in the source schema that is within a **Choice** node. Because the indicated node in the source schema may not appear in an input instance message, there may not be a source from which to create the required node in the destination schema.  
  
 **User Action**  
  
 As appropriate, either change the indicated node in the destination schema to optional, or provide a different source for the indicated node in the destination schema that must occur in all valid input instance messages.
