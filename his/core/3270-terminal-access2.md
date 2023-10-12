---
description: "Learn more about: 3270 Terminal Access"
title: "3270 Terminal Access2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# 3270 Terminal Access
Users or groups who require access to 3270 sessions from workstations using Host Integration Server client applications must be members of the SNA subdomain. Therefore, they are also members of the Windows domain of which the subdomain is a part.  
  
 Once enrolled in the SNA subdomain, you can assign specific 3270 (LU type 2) resources to the appropriate accounts. The users can access only the specific resources you allocate to them.  
  
 The preferred method for maintaining security in your environment is by using domain security to authenticate users, and then limiting their access by assigning them only specified resources.  
  
## See Also  
 [Resource Security](../core/resource-security1.md)
