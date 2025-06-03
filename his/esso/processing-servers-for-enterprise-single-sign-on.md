---
description: "Learn more about: Processing Servers for Enterprise Single Sign-On"
title: "Processing Servers for Enterprise Single Sign-On"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Processing Servers for Enterprise Single Sign-On
In a multicomputer environment, after the master secret server and Single Sign-On (SSO) database have been created, you can install Enterprise Single Sign-On on subsequent computers. These are typically the computers on which either BizTalk Server or Host Integration Server is installed as well.  
  
 The initial installation process is the same as on the first computer. Configuration, however, becomes slightly different. Because the master secret server and the SSO database are already in place, select **Join** when the Configuration Wizard asks the question, **Create a new SSO system or Join an existing system?**  
  
> [!NOTE]
>  During configuration, it is possible for a group on one computer to join an SSO database on a different computer that is not in the database configured for that group. Although this is possible, it is not recommended.  
  
## See Also  
 [Upgrading from Host Integration Server 2000 or SNA Server 4.0](../esso/upgrading-from-host-integration-server-2000-or-sna-server-4-0.md)
