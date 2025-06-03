---
description: "Learn more about: Processing Servers for SSO"
title: "Processing Servers for SSO"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Processing Servers for SSO
In a multi-computer environment, after the master secret server and SSO database have been created, you can install Enterprise Single Sign-On on subsequent computers. These are typically the computers on which either BizTalk Server or Host Integration Server is installed as well.  
  
 The initial installation process is the same as on the first computer. Configuration, however, becomes slightly different. Since the master secret server and the SSO database are already in place, select **Join** when the Configuration Wizard asks, **Create a new SSO system** or **Join an existing system**.  
  
 Note that it is possible during configuration for a group on one computer to join an SSO database on a different computer that is not the database configured for that group. While this is possible, it is not recommended.  
  
## See Also  
 [Upgrading from a Previous Version of SSO](../core/upgrading-from-a-previous-version-of-sso.md)
