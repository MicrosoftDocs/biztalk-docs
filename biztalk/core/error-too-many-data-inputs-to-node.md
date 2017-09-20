---
title: "Error - Too Many Data Inputs to Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.tooManyDataInputsToNode"
ms.assetid: 176805f0-2d6d-4072-b866-132b98c7e4b5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Too Many Data Inputs to Node
**Error Code**  
  
 btm1005  
  
 **Explanation**  
  
 There are a greater number of links connected to the indicated node in the destination schema than the number of input links to the **Looping** functoid that is connected to an ancestor node of the indicated node. The number of links of the former and latter types should match.  
  
 **User Action**  
  
 Rework the number of links connected to the indicated node and to the **Looping** functoid connected to the ancestor node so that they match.