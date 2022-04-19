---
description: "Learn more about: RH Usage Errors (Category X&#39;40&#39;)"
title: "RH Usage Errors (Category X&#39;40&#39;)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1445313-cd22-452d-9492-c4384f4416f7
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# RH Usage Errors (Category X&#39;40&#39;)
These sense codes indicate that fields in the request/response header (RH) are contrary to SNA rules or previously selected BIND options and prevent the intended half-session from receiving the request.  
  
 The checks 400A and 4012 are also performed. These do not permit negative responses because they apply to no-response sessions and responses, respectively.  
  
 The following codes are in this category.  
  
|Code|Meaning|  
|----------|-------------|  
|4006|Exception response not allowed|  
|4007|Definite response not allowed|  
|400F|Incorrect use of format indicator|  
|4011|Incorrect specification of RU category|  
|4014|Incorrect use of DR1, DR2, ER|  
  
## See Also  
 [SNA Sense Codes](../core/sna-sense-codes1.md)
