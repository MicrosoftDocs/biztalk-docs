---
description: "Learn more about: Error - Too Many Data Inputs to Node"
title: "Error - Too Many Data Inputs to Node"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.tooManyDataInputsToNode"
---
# Error - Too Many Data Inputs to Node
**Error Code**  
  
 btm1005  
  
 **Explanation**  
  
 There are a greater number of links connected to the indicated node in the destination schema than the number of input links to the **Looping** functoid that is connected to an ancestor node of the indicated node. The number of links of the former and latter types should match.  
  
 **User Action**  
  
 Rework the number of links connected to the indicated node and to the **Looping** functoid connected to the ancestor node so that they match.
