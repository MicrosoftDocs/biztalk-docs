---
title: "LU Groups1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c62b7c3-1dd3-40ec-9e19-98d812371d7b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# LU Groups
Note that Host Integration Server supports logical unit (LU) groups. An LU group consists of a number of LUs of the same type, such as 3270 display LUs or logical unit application (LUA) LUs. Any of the LUs in the group can be used for the same task.  
  
 If an application sends an [Open(SSCP) Request](../core/open-sscp-request1.md) specifying the name of a 3270 display LU group, the local node can select any LU within the group to be used by the application. LUA LU groups are used in the same way, except that the application can specify either the name of the group or the name of any LU within the group to access the group.  
  
## See Also  
 [Resource Location for Open SSCP](../core/resource-location-for-open-sscp2.md)