---
title: "Error - Map Without Any Links or Constants | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.mapWithoutAnyLinksOrConstants"
ms.assetid: 8d1cdbcd-4bd0-4ddc-9e94-746e82b6ec48
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Map Without Any Links or Constants
**Error Code**  
  
 btm1000  
  
 **Explanation**  
  
 The map does not contain any links between the schemas, or constant values in the destination schema. Therefore, no output can be created from this map.  
  
 **User Action**  
  
 Add the appropriate links and, if appropriate, functoids to the map grid, or constants to the destination schema, to specify how instance messages conforming to the source schema should be transformed into instance messages conforming to the destination schema.