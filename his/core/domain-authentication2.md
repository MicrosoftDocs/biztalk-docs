---
title: "Domain Authentication2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 245319a1-a92f-4081-8f51-4a772a70a6a2
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Domain Authentication
A *domain*, as it pertains to Windows, is a group of computers that share a network resource database and have a common security policy. A Windows domain contains a *primary domain controller* (PDC) computer that acts as the resource and user manager for the entire domain. One or more computers in the domain can be configured to act as a *backup domain controller* (BDC). The BDC can take over for the PDC should any problems arise. The remaining computers in the domain are user workstations or servers that provide resources to domain users.  
  
 Within a Windows domain, Host Integration Server computers are logically grouped into an entity called a *subdomain*. Each SNA subdomain can contain up to 15 Host Integration Server computers, and a Windows domain can contain an unlimited number of subdomains. It is common to have multiple domains that manage user accounts independently of one another.  
  
 The domain model provides two key advantages over peer-to-peer networks with regards to security:  
  
- You can manage user accounts from a central location.  
  
- You can set up one unified security system for all user accounts in the domain.  
  
  Host Integration Server relies on the PDC or BDC to provide authentication services to users requesting access to host resources. Only users who have been validated by the PDC or BDC can gain access to resources provided by servers in the subdomain.  
  
  You can use domain authentication to verify users who request resources provided by these services:  
  
- 3270 or 5250 terminal access from workstations using Host Integration Server client software  
  
- APPC, CPI-C, or LUA applications built using Host Integration Server APIs  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)   
 [Authentication](../core/authentication1.md)   
 [Workstation Authentication](../core/workstation-authentication1.md)