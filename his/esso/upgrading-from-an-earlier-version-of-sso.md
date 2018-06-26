---
title: "Upgrading from an Earlier Version of SSO | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12c04ac5-c8f5-4d6c-ae2e-e5c479be27d2
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Upgrading from an Earlier Version of SSO
If you are installing the Enterprise Single Sign-on (SSO) feature, and you already have an earlier version deployed on your computer (for example, from [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] CTP, or Microsoft BizTalk Server), you must follow these steps.  
  
- Back up the SSODB to a secure location.  
  
- Back up the master secret key on the master secret server.  
  
- Update the master secret server by running [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup, selecting **Custom Installation**, and then selecting **Enterprise Single Sign-On**. After selecting **Enable Enterprise Single Sign-On on this computer**, select **Join an existing SSO system**.  
  
  You do not have to update the other SSO servers (non-master secret servers) from your BizTalk Server installation. However, if you want the new Enterprise Single Sign-On features to be available on those servers, you must update them by using the same procedures outlined earlier.  
  
> [!NOTE]
>  These considerations also apply if you are installing Microsoft BizTalk Server 2006 on a computer that has an existing installation of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Enterprise Single Sign-On, and you want to update the servers.  
  
## See Also  
 [Upgrading from Host Integration Server 2000 or SNA Server 4.0](../esso/upgrading-from-host-integration-server-2000-or-sna-server-4-0.md)   
 [Using Host-Initiated SSO functionality in Enterprise Single Sign-On](../esso/using-host-initiated-sso-functionality-in-enterprise-single-sign-on.md)   
 [Processing Servers for Enterprise Single Sign-On](../esso/processing-servers-for-enterprise-single-sign-on.md)