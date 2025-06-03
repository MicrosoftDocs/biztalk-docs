---
description: "Learn more about: Providing Hot Backup"
title: "Providing Hot Backup2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Providing Hot Backup
In the IBM i environment, Host Integration Server uses a combination of LU names and LU aliases over one or more servers to achieve transparent connections with hot backup to an IBM i.  
  
## Hot backup connections to an IBM i  
 A single Host Integration Server computer can use multiple connections to provide hot backup. To use this method, two or more APPC connections to the same IBM i are configured and appropriate LUs are grouped into a pool. If one of the connections fails, the clients can reconnect to the IBM i without reconfiguration.  
  
 Host Integration Server can also use multiple Host Integration Server computers as backups to one another. If one of the servers fails, the clients are shifted from the failed server to a working server. Use a combination of connections and servers with hot backup to maintain a high level of host availability in your enterprise.  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)
