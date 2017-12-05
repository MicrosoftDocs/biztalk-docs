---
title: "Protect TI from Unauthorized Mainframe or AS-400 Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 591c3018-6d15-4565-9ba5-79f66cc1251f
caps.latest.revision: 5
---
# Protect TI from Unauthorized Mainframe or AS/400 Access
To prevent an attacker from using the mainframe or AS/400 connection to access the server running Transaction Integrator, you should:  
  
-   Utilize direct network connections over private segment.  
  
-   Use IPsec, where supported, for IP communications between the host and Windows servers.  
  
-   For SNA LU6.2 network connections to mainframe or AS/400 computers, use Host Integration Server server-to-server data encryption when deploying upstream Host Integration Server computer as SNA gateway to downstream TI HIP computer.  
  
-   For SNA LU6.2 network connections to mainframe, use Host Integration Server IP-DLC Link Service in conjunction with IPsec.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation1.md)   
 [Introduction to the IP-DLC Link Service](../core/introduction-to-the-ip-dlc-link-service2.md)   
 [Secure Deployment of the IP-DLC Link Service](../core/secure-deployment-of-the-ip-dlc-link-service1.md)