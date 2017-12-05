---
title: "Web-to-Host Load Balancing2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9436e4db-f495-4b98-8c15-495dccf670c3
caps.latest.revision: 4
---
# Web-to-Host Load Balancing
Internet Information Services (IIS) can use Windows Network Load Balancing (NLB) to provide load balancing and fail-over support for incoming HTTP requests. NLB is a TCP/IP-based load balancing solution that load balances incoming TCP/IP packets to all nodes in a cluster or to a single node in a cluster. NLB distributes the load across identical servers.  
  
 The [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] clients and Web browsers go through IIS to gain access to the Active Server Pages (ASP) that invoke the Transaction Integrator (TI) methods that call the CICS or IMS transaction program (TP).  
  
 NLB provides high availability on enterprise systems. It detects connection failures and automatically redirects requests to other nodes in the server farm. NLB also improves performance when all incoming packets are load balanced between various nodes in the server farm based on server load.  
  
 You can configure NLB to balance the load on multiple servers that use single affinity, no affinity, or Class C. No affinity distributes all incoming TCP/IP requests across any node in the NLB server farm, which can increase the number of requests that need to be redirected because there is no concept of a session state. We recommend that you use IIS to distribute HTTP requests configured for single affinity. When the server is configured for single affinity, all incoming packets using the NLB virtual IP address are locked to a specific node in the server farm. Every packet that is sent from the client using the cluster IP address will connect to that node.  
  
> [!NOTE]
>  NLB cannot detect whether the TI Automation server fails to respond. It can only detect if the server fails, for example if TCP/IP does not respond.  
  
## See Also  
 [Load Balancing and Hot Backup](../core/load-balancing-and-hot-backup1.md)