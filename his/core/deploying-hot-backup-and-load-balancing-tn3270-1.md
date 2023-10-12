---
description: "Learn more about: Deploying Hot Backup and Load Balancing (TN3270)"
title: "Deploying Hot Backup and Load Balancing (TN3270)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Deploying Hot Backup and Load Balancing (TN3270)
A Windows domain can contain one or more Host Integration Server subdomains. Like 3270 LUs, LUA LUs from multiple servers in different subdomains can be assigned to the TN3270 service. This lets you distribute client sessions among the participating servers in the subdomain, thereby balancing the load.  
  
 Creating redundant connections to the mainframe and assigning them to a TN3270 service increases service availability. If one server goes down, a client can still access LUA LUs on a different server. Similarly, a single server can be configured with redundant host links to increase hot backup and bandwidth if no other Host Integration Server computers are available.  
  
## See Also  
 [Setting Port Numbers (TN3270)](../core/setting-port-numbers-tn3270-1.md)   
 [Assigning LUs to an IP Address (TN3270)](../core/assigning-lus-to-an-ip-address-tn3270-1.md)   
 [Deployment Strategies (TN3270)](../core/deployment-strategies-tn3270-2.md)
