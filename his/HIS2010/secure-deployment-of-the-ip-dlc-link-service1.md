---
title: "Secure Deployment of the IP-DLC Link Service1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb314a0e-befc-4c42-82d3-4435a11e7e23
caps.latest.revision: 4
---
# Secure Deployment of the IP-DLC Link Service
The IP-DLC link service takes advantage of the entire [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] secure deployment feature set, especially the following:  
  
-   A typical IP-DLC link service deployment scenario may use Internet Protocol security (IPsec), a firewall, or a virtual private network (VPN) as a security barrier between the Host Integration Server computer and the remote node. (A VPN is advisable if the HPR/IP link spans an insecure IP network.)  
  
-   Incoming frames from IP addresses that are not already defined in Host Integration Server are rejected. This isolates the main SNA node service from such attack.  
  
-   The IP-DLC link service checks the length of incoming datagrams before copying the data into internal data areas, and discards any that are too long.  
  
-   All configuration data—whether from registry entries, COM.cfg, or the SNA node service—is validated for correct value when first accessed. Particular consideration is given to validating lengths to avoid buffer overruns. If any errors are found, the IP-DLC link service logs an event and terminates.  
  
## See Also  
 [Creating an IP-DLC Connection](../HIS2010/creating-an-ip-dlc-connection2.md)   
 [Viewing Connections](../HIS2010/viewing-connections2.md)   
 [Defining Dependent LUs](../HIS2010/defining-dependent-lus2.md)   
 [Connections and the SnaCfg Utility](../HIS2010/connections-and-the-snacfg-utility2.md)