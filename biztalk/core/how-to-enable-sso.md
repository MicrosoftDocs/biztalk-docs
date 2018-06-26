---
title: "How to Enable SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications [SSO], creating"
  - "SSO, enabling"
  - "maps [SSO], creating"
  - "managing [SSO], enabling"
  - "SSO, maps"
  - "SSO, applications"
  - "creating, applications [SSO]"
  - "managing [SSO], creating affiliate applications"
ms.assetid: dda89d15-6b70-4c40-b658-2f6cbdd545c8
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable SSO
You can enable the entire Enterprise Single Sign-On (SSO) system by using either the MMC Snap-In or the command line.  
  
 After you run the enabling command, there is a short delay before all Single Sign-On Servers are enabled, as each polls the SSO database for the latest global information.  
  
 If you want to configure affiliate applications and mappings in the SSO system, you must also create an affiliate application. After an SSO affiliate administrator creates an affiliate application, an application administrator can make changes to it, and application users (end-users) can create their own mappings. For more information, see [Managing Affiliate Applications](../core/managing-affiliate-applications.md) and [Managing User Mappings](../core/managing-user-mappings.md).  
  
### To enable the SSO system using the MMC Snap-In  
  
1.  Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Enable**.  
  
### To enable the SSO system using the command line  
  
1.  Click **Start**, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –enablesso**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To enable SSO to create affiliate applications and mappings  
  
1. Log on as an SSO administrator or SSO affiliate administrator to the SSO Server, or on a computer that has the SSO administration sub services of SSO.  
  
2. On the **Start** menu, click **Run**, and then type **cmd**.  
  
3. At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4. Type **ssomanage -enablesso** to enable the Enterprise Single Sign-On service.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
5. Log on as an SSO affiliate administrator.  
  
6. Type **ssomanage -createapps *\<application file\>*** to create an affiliate application, where \<application file\> is the XML file that contains definitions for the affiliate applications.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Set the SSO Server](../core/how-to-set-the-sso-server.md)   
 [How to Disable SSO](../core/how-to-disable-sso.md)   
 [How to Update the SSO Database](../core/how-to-update-the-sso-database.md)   
 [Using SSO](../core/using-sso.md)