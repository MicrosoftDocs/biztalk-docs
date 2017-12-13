---
title: "Providing Hot Backup2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64db7ef6-dadc-4691-8cd7-6feb04a6b74c
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Providing Hot Backup
In the AS/400 environment, Host Integration Server uses a combination of LU names and LU aliases over one or more servers to achieve transparent connections with hot backup to an AS/400.  
  
## Hot backup connections to an AS/400  
 A single Host Integration Server computer can use multiple connections to provide hot backup. To use this method, two or more APPC connections to the same AS/400 are configured and appropriate LUs are grouped into a pool. If one of the connections fails, the clients can reconnect to the AS/400 without reconfiguration.  
  
 Host Integration Server can also use multiple Host Integration Server computers as backups to one another. If one of the servers fails, the clients are shifted from the failed server to a working server. Use a combination of connections and servers with hot backup to maintain a high level of host availability in your enterprise.  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)