---
title: "Deploying Hot Backup and Load Balancing (TN3270)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0dda96d-0d0e-4b10-b219-b6f6a4336602
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Deploying Hot Backup and Load Balancing (TN3270)
A Windows domain can contain one or more Host Integration Server subdomains. Like 3270 LUs, LUA LUs from multiple servers in different subdomains can be assigned to the TN3270 service. This lets you distribute client sessions among the participating servers in the subdomain, thereby balancing the load.  
  
 Creating redundant connections to the mainframe and assigning them to a TN3270 service increases service availability. If one server goes down, a client can still access LUA LUs on a different server. Similarly, a single server can be configured with redundant host links to increase hot backup and bandwidth if no other Host Integration Server computers are available.  
  
## See Also  
 [Setting Port Numbers (TN3270)](../core/setting-port-numbers-tn3270.md)   
 [Assigning LUs to an IP Address (TN3270)](../core/assigning-lus-to-an-ip-address-tn3270.md)   
 [Deployment Strategies (TN3270)](../core/deployment-strategies-tn3270.md)