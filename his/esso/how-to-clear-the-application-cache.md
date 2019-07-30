---
title: "How to Clear the Application Cache | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a897791-d32f-46a4-8c5d-2b2161e92bd9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Clear the Application Cache
Use the MMC Snap-In or the **purgecache** command to remove the contents of the credential cache (all the information that is associated with the affiliate application) for the specified application on all Single Sign-On (SSO) servers.  
  
### To clear the cache using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Click **Affiliate Applications**.  
  
4.  In the results pane, right-click the affiliate application, and click **Clear**.  
  
### To clear the cache using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –purgecache <application name>`, where \<*application name*> is the name of the affiliate application that you want to purge the cache for.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)