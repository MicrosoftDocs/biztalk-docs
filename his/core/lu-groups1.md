---
description: "Learn more about: LU Groups"
title: "LU Groups1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LU Groups
Note that Host Integration Server supports logical unit (LU) groups. An LU group consists of a number of LUs of the same type, such as 3270 display LUs or logical unit application (LUA) LUs. Any of the LUs in the group can be used for the same task.  
  
 If an application sends an [Open(SSCP) Request](./open-sscp-request2.md) specifying the name of a 3270 display LU group, the local node can select any LU within the group to be used by the application. LUA LU groups are used in the same way, except that the application can specify either the name of the group or the name of any LU within the group to access the group.  
  
## See Also  
 [Resource Location for Open SSCP](../core/resource-location-for-open-sscp2.md)
