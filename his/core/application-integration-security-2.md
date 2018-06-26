---
title: "Application Integration (Security)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dc24c76-5d46-4aac-82b9-2b27af821389
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Application Integration (Security)
Security affects Transaction Integrator (TI) in two ways. First, TI components can be assigned security attributes in the same way as other COM+ components. This requires no TI development. Second, the TI run-time environment needs to deal with the security mechanisms of the remote environment (RE). TI provides two security options with an optional override for each:  
  
- Package-level (also known as application-level)  
  
- 4User-level  
  
- Optional explicit-level override  
  
  When configured for user-level credentials, TI makes use of the APPC Privileged Proxy feature for single sign on. This requires that the user context that the APPC application (TI, in this case) is running under be a member of the **HSDomain_Proxy** group. (The **HSDomain_Proxy** group is one of the two groups created when the host security domain is created.) By default, the **HSDomain_Proxy** group contains the **Domain Admins** group. If TI is not running under the context of a user in the **Domain Admins** group, you will need to add the user to the **HSDomain_Proxy** group.  
  
  When deploying a TI component, the administrator must choose either package-level security or user-level security as the default. The optional explicit-level security override is a separate option that the administrator can enable or disable; the override applies regardless of which security option (package-level or user-level) is in place. If the explicit-level override is disabled, base applications will not be permitted to use the callback to provide user credentials. The administrator can also turn on the optional Already Verified settings.  
  
## In This Section  
 [Single Sign-On in Transaction Integrator](../core/single-sign-on-in-transaction-integrator2.md)  
  
 [Special Security Settings for TCP/IP](../core/special-security-settings-for-tcp-ip1.md)  
  
 [Mainframe Authentication for CICS LINK](../core/mainframe-authentication-for-cics-link1.md)  
  
 [AS/400 Security](../core/as-400-security1.md)  
  
 [Limitations of User Access Level Sign On](../core/limitations-of-user-access-level-sign-on1.md)  
  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)  
  
## See Also  
 [Security and Protection](../core/security-and-protection1.md)