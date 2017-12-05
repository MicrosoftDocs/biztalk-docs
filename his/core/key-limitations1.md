---
title: "Key Limitations1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 493b107d-0a45-4994-ada1-fc3afcbb358e
caps.latest.revision: 3
---
# Key Limitations
The key limitations with the IP-DLC link service implementation are as follows:  
  
-   The IP-DLC link service cannot be run as a distributed link service (DLS).  
  
-   The PU Passthrough and Downstream connections are not supported over IP-DLC connections. It is not possible to have a one-to-one correspondence between upstream and downstream messages where the upstream connection is an IP-DLC connection.  
  
-   Each IP-DLC link service must use a different CP name from the SNA node service.  
  
-   Each IP-DLC link service requires a unique local IP address. If multiple IP-DLC link services are required, each must have its own unique local IP address.  
  
-   A single IP-DLC link service cannot be shared by multiple SNA node services. Each SNA node service must use a different IP-DLC link service for IP-DLC connectivity.  
  
## See Also  
 [System Overview](../core/system-overview2.md)   
 [Supported Features](../core/supported-features1.md)   
 [Scalability](../core/scalability2.md)   
 [Key Limitations](#his_ip_dlc_introduction_to_the_ip_dlc_link_service_daan)