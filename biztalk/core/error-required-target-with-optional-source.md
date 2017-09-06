---
title: "Error - Required Target with Optional Source | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.reqdTargetWithOptionalSource"
ms.assetid: 3f342011-4577-4682-8324-8296615d5194
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Required Target with Optional Source
**Error Code**  
  
 btm1001  
  
 **Explanation**  
  
 The data for the indicated required node in the destination schema comes from an optional node in the source schema. Therefore, there may be valid instance messages for which mapping will fail.  
  
 **User Action**  
  
 Confirm the optional and required characteristics of the specified source and destination nodes, respectively, and consider making these characteristics match.