---
description: "Learn more about: Error - Too Many Logical Inputs to Node"
title: "Error - Too Many Logical Inputs to Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.tooManyLogicalInputsToNode"
ms.assetid: 9295d6a2-702d-4cf3-8f5d-26ba63b9fce0
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Too Many Logical Inputs to Node
**Error Code**  
  
 btm1006  
  
 **Explanation**  
  
 There are a greater number of logical links connected to the indicated node in the destination schema than the number of input links to the **Looping** functoid that is connected to an ancestor node of the indicated node. The number of links of the former and latter types should match.  
  
 **User Action**  
  
 Rework the number of links connected to the indicated node and to the **Looping** functoid connected to the ancestor node so that they match.
