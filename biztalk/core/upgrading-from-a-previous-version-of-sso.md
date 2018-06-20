---
title: "Upgrading from a Previous Version of SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "upgrading, SSO"
  - "SSO, upgrading"
ms.assetid: 78b99d99-9a10-4453-9db5-ae1bacd7de50
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Upgrading from a Previous Version of SSO
If you are installing the Enterprise Single Sign-on feature and you already have a previous version deployed on your computer (for example, from Microsoft BizTalk Server 2009), you must complete the steps below.  
  
1. Back up the SSO database to a secure location  
  
2. Back up the master secret key on the master secret server  
  
3. Update the master secret server by running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup, choosing **Custom Installation**, and then selecting **Enterprise Single Sign-On**.  
  
4. After selecting **Enable Enterprise Single Sign-on on this computer**, select **Join an existing SSO system**.  
  
   It is not necessary to update the other SSO servers (non-master secret servers) from your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation. However, if you want the new Enterprise Single Sign-On features to be available on those servers, you must update them by using the same procedure outlined above.  
  
> [!NOTE]
>  These considerations also apply if you are installing Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a computer with an existing installation of Host Integration Server 2009 Enterprise Single Sign-On, and you want to update the servers.  
  
 If you are installing Host Integration Server on a computer where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is already installed, do not select the Enterprise Single Sign-On feature.  
  
## In This Section  
  
-   [Using Host Initiated SSO Functionality](../core/using-host-initiated-sso-functionality.md)  
  
-   [Processing Servers for SSO](../core/processing-servers-for-sso.md)