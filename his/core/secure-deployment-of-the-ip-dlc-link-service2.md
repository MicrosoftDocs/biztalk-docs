---
description: "Learn more about: Secure Deployment of the IP-DLC Link Service"
title: "Secure Deployment of the IP-DLC Link Service2"
ms.custom: ""
ms.date: "01/26/2024"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Secure Deployment of the IP-DLC Link Service
The IP-DLC link service takes advantage of the entire [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] secure deployment feature set, especially the following:  
  
-   A typical IP-DLC link service deployment scenario may use Internet Protocol security (IPsec), a firewall, a virtual private network (VPN) or an Azure ExpressRoute circuit as a security barrier between the Host Integration Server computer and the remote node. (An Azure ExpressRoute circuit or a VPN are advisable if the HPR/IP link spans a potential insecure IP network.)
  
-   Incoming frames from IP addresses that are not already defined in Host Integration Server are rejected. This isolates the main SNA node service from such attack.  
  
-   The IP-DLC link service checks the length of incoming datagrams before copying the data into internal data areas, and discards any that are too long.  
  
-   All configuration data—whether from registry entries, COM.cfg, or the SNA node service—is validated for correct value when first accessed. Particular consideration is given to validating lengths to avoid buffer overruns. If any errors are found, the IP-DLC link service logs an event and terminates.  
  
## See Also  
 [Creating an IP-DLC Connection](../core/creating-an-ip-dlc-connection1.md)   
 [Viewing Connections](../core/viewing-connections1.md)   
 [Defining Dependent LUs](../core/defining-dependent-lus1.md)   
 [Connections and the SnaCfg Utility](../core/connections-and-the-snacfg-utility1.md)
