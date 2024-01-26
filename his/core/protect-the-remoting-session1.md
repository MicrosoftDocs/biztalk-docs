---
description: "Learn more about: Protect the Remoting Session"
title: "Protect the Remoting Session1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Protect the Remoting Session
To prevent an attacker from tampering with the remote session or denying service, you should do the following:  
  
- Use HTTPS between the remoting client and the server  
  
- Use separate ASP.NET application contexts for various levels of privileged users, thereby preventing lower-privileged users from affecting sessions belonging to higher-privileged users.  
  
  You can also help mitigate this threat with the following deployment scenario:  
  
- ASP.NET Web client.  
  
  You can learn more about this threat by reading about the following:  
  
- Multiple levels of authorized users  
  
- ASP.NET application and IIS security  
  
- Properly-formatted TRM, DPL, SNA, IP, and other messages  
  
- Valid host user ID and password  
  
- Valid Windows user ID for Single Sign-On (SSO).  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)
