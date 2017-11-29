---
title: "Processing Servers for Enterprise Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a4f35cf-8ad1-4965-b2b0-46e0e422bca9
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Processing Servers for Enterprise Single Sign-On
In a multicomputer environment, after the master secret server and Single Sign-On (SSO) database have been created, you can install Enterprise Single Sign-On on subsequent computers. These are typically the computers on which either BizTalk Server or Host Integration Server is installed as well.  
  
 The initial installation process is the same as on the first computer. Configuration, however, becomes slightly different. Because the master secret server and the SSO database are already in place, select **Join** when the Configuration Wizard asks the question, **Create a new SSO system or Join an existing system?**  
  
> [!NOTE]
>  During configuration, it is possible for a group on one computer to join an SSO database on a different computer that is not in the database configured for that group. Although this is possible, it is not recommended.  
  
## See Also  
 [Upgrading from Host Integration Server 2000 or SNA Server 4.0](../esso/upgrading-from-host-integration-server-2000-or-sna-server-4-0.md)