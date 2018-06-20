---
title: "How to Clear the Application Cache | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "caching, applications"
  - "managing [SSO applications], clearing cache"
  - "applications [SSO], caching"
ms.assetid: 6230b9a4-c7b8-47b4-854b-12853d9bf5b0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Clear the Application Cache
You can use the MMC Snap-In or the command line to remove the contents of the credential cache (all the information associated with the affiliate application) for the specified application on all of the Single Sign-On Servers.  
  
### To clear the cache using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Click **Affiliate Applications**.  
  
4.  In the results pane, right-click the affiliate application, and click **Clear**.  
  
### To clear the cache using the command line  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type <strong>ssomanage –purgecache *\<application name\></strong><em>, where \<</em>application name*\> is the name of the affiliate application you want to purge the cache for.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)