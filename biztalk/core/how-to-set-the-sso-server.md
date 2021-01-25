---
description: "Learn more about: How to Set the SSO Server"
title: "How to Set the SSO Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servers, selecting [SSO]"
  - "SSO, selecting servers"
  - "managing [SSO], selecting servers"
  - "SSOManage [SSO]"
ms.assetid: a0b0176d-b426-4ab1-8a7e-1f96f4214683
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set the SSO Server
Each time you use ssomanage, you must first point the user to the Single Sign-On server you want to connect to.  
  
 You can do this in one of two ways:  
  
-   Individual users can point themselves to the correct Single Sign-On Server.  
  
-   A local computer administrator for the Single Sign-On server can point all the members of the Single Sign-On Users account to this server.  
  
### To set the Enterprise Single Sign-On Server using the MMC Snap-In  
  
1.  Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.  
  
3.  Browse to the desired server.  
  
4.  If appropriate, select the **Set SSO Server for all users** check box.  
  
5.  Click **OK**.  
  
### To set the Enterprise Single Sign-On Server for a single user using the command line  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –server \<SSO server name\>**, where **\<SSO server name\>** is the computer name of the Single Sign-On Server the user wants to connect to.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To set the Enterprise Single Sign-On Server for all users using the command line  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –serverall \<SSO server name\>**, where **\<SSO server name\>** is the computer name of the Single Sign-On Server all members of the Single Sign-On Users account will be pointed to.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To determine the Enterprise Single Sign-On Server to which a user is connected using the command line  
  
1.  On the **Start** menu, click **run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –showserver**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
> [!NOTE]
>  This command displays the settings for the current user as well as for other users if they exist.  
  
## See Also  
 [How to Enable SSO](../core/how-to-enable-sso.md)   
 [How to Disable SSO](../core/how-to-disable-sso.md)   
 [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md)   
 [Using SSO](../core/using-sso.md)
