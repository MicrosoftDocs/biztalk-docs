---
title: "Error - Children of Mass Copy Functoid Generate Code | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.massCopyChildtenGenCode"
ms.assetid: c791009b-241b-4004-b0c6-f1536bb119c5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Children of Mass Copy Functoid Generate Code
**Error Code**  
  
 btm1068  
  
 **Explanation**  
  
 A scenario that contradicts the functionality of the **Mass Copy** functoid was found in the map. In the destination schema, descendent nodes of a node that is linked to the output of a **Mass Copy** functoid are attempting to generate XSLT code of their own.  
  
 **User Action**  
  
 Remove the incompatibility by changing the usage of the relevant **Mass Copy** functoid or changing the child nodes such that they no longer generate XSLT code of their own.