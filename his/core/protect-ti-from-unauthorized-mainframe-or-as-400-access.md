---
title: "Protect TI from Unauthorized Mainframe or AS-400 Access1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc201817-b8a4-455e-96ee-ccda4785b3b1
caps.latest.revision: 4
---
# Protect TI from Unauthorized Mainframe or AS/400 Access
To prevent an attacker from using the mainframe or AS/400 connection to access the server running Transaction Integrator, you should:  
  
-   Utilize direct network connections over private segment.  
  
-   Use IPsec, where supported, for IP communications between the host and Windows servers.  
  
-   For SNA LU6.2 network connections to mainframe or AS/400 computers, use Host Integration Server server-to-server data encryption when deploying upstream Host Integration Server computer as SNA gateway to downstream TI HIP computer.  
  
-   For SNA LU6.2 network connections to mainframe, use Host Integration Server IP-DLC Link Service in conjunction with IPsec.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation.md)   
 [Introduction to the IP-DLC Link Service](../core/introduction-to-the-ip-dlc-link-service.md)   
 [Secure Deployment of the IP-DLC Link Service](../core/secure-deployment-of-the-ip-dlc-link-service.md)