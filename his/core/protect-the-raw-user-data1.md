---
description: "Learn more about: Protect the Raw User Data"
title: "Protect the Raw User Data1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Protect the Raw User Data
To prevent an attacker from reading data packets on the network and either tampering with the data or disclosing the data, or to prevent an attacker from denying service, you should:  
  
-   Place the computer running Transaction Integrator (TI) and the host in a secure location.  
  
-   Use direct network connections over a private segment  
  
-   Use IPsec, where supported, for IP communications between host and Windows servers  
  
-   For SNA LU6.2 network connections to mainframe or IBM i computers, use Host Integration Server server-to-server data encryption when deploying upstream an Host Integration Server computer as a SNA gateway to a downstream TI HIP computer  
  
-   For SNA LU6.2 network connections to mainframe, use Host Integration Server IP-DLC Link Service in conjunction with IPsec.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)   
 [Configuring an IP-DLC Link Service](./configuring-an-ip-dlc-link-service1.md)
