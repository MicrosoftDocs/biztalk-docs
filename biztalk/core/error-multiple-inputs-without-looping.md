---
description: "Learn more about: Error - Multiple Inputs Without Looping"
title: "Error - Multiple Inputs Without Looping"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.multipleInputsWithoutLooping"
---
# Error - Multiple Inputs Without Looping
**Error Code**  
  
 btm1004  
  
 **Explanation**  
  
 Multiple links are connected to the indicated node in the destination schema, which is only valid when one of the ancestor nodes of the indicated node is connected to a **Looping** functoid.  
  
 **User Action**  
  
 Either remove all but one of the links to the indicated node in the destination schema, or connect one of the ancestor nodes of the indicated node to a looping functoid.
