---
title: "Request Errors (Category X&#39;10&#39;)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b99f3f2d-00b0-4df3-b8f1-07cbbf14b021
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Request Errors (Category X&#39;10&#39;)
Sense codes in this category represent an imbalance in half-session capabilities. They indicate that the RU (request/response unit) was delivered to the intended half-session but could not be processed. The following codes are in this category.  


| Code |                                                                             Meaning                                                                             |
|------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1003 | Function not supported (also used instead of X'0826', which is not supported by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]) |
| 1005 |                                                        Parameter modifying a control function is invalid                                                        |
| 1007 |                                                       Category not supported (SSCP data for host printer)                                                       |

## See Also  
 [SNA Sense Codes](../core/sna-sense-codes1.md)