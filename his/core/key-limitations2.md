---
description: "Learn more about: Key Limitations"
title: "Key Limitations2"
ms.custom: ""
ms.date: "12/13/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Key Limitations
The key limitations with the IP-DLC link service implementation are as follows:  
  
-   The IP-DLC link service cannot be run as a distributed link service (DLS).  
  
-   Each IP-DLC link service must use a different CP name from the SNA node service.  
  
-   Each IP-DLC link service requires a unique local IP address. If multiple IP-DLC link services are required, each must have its own unique local IP address.  
  
-   A single IP-DLC link service cannot be shared by multiple SNA node services. Each SNA node service must use a different IP-DLC link service for IP-DLC connectivity.  
  
## See Also  
 [System Overview](../core/system-overview1.md)   
 [Supported Features](../core/supported-features2.md)   
 [Scalability](../core/scalability1.md)   
