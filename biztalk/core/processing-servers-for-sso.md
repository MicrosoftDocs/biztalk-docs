---
title: "Processing Servers for SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, processing servers"
  - "processing servers [SSO]"
ms.assetid: 9e80a456-974a-49b3-bb64-2e4713036cfb
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing Servers for SSO
In a multi-computer environment, after the master secret server and SSO database have been created, you can install Enterprise Single Sign-On on subsequent computers. These are typically the computers on which either BizTalk Server or Host Integration Server is installed as well.  
  
 The initial installation process is the same as on the first computer. Configuration, however, becomes slightly different. Since the master secret server and the SSO database are already in place, select **Join** when the Configuration Wizard asks, **Create a new SSO system** or **Join an existing system**.  
  
 Note that it is possible during configuration for a group on one computer to join an SSO database on a different computer that is not the database configured for that group. While this is possible, it is not recommended.  
  
## See Also  
 [Upgrading from a Previous Version of SSO](../core/upgrading-from-a-previous-version-of-sso.md)