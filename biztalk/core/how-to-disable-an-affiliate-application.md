---
title: "How to Disable an Affiliate Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "disabling, applications"
  - "managing [SSO applications], disabling"
  - "applications [SSO], disabling"
ms.assetid: febf1687-f0d0-4f87-b462-23535bbddf6d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Disable an Affiliate Application
You can use the MMC Snap-In or the command line to disable the specified affiliate application.  
  
### To disable an affiliate application using the MMC Snap-In  
  
1.  On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click the affiliate application, and then click **Disable**.  
  
### To disable an affiliate application using the command line  
  
1. Click **Start**, click **run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type <strong>ssomanage –disableapp *\<application name\></strong><em>, where \<</em>application name*\> is the name of the affiliate application you want to disable.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)