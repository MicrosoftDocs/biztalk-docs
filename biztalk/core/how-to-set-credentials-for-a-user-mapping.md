---
title: "How to Set Credentials for a User Mapping | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps [SSO], credentials"
  - "managing [SSO maps], configuring credentials"
ms.assetid: 75b29114-56b6-4db0-8666-61cf6c675401
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Credentials for a User Mapping
Use this command to set the credentials for a user to access a specific application.  
  
 This command does not display the password as you type it.  
  
 If the user mapping already exists, this command sets the credentials for that existing mapping. If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.  
  
### To set credentials for a user mapping  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –setcredentials \<domain>\\<username\> \<applicationname>**, where **\<domain>** is the Windows domain for the user account, **\<username>** is the Windows user name, and **\<applicationname>** is the specific application for which you want to set the credentials for.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4.  When the SSO system prompts you for the user credentials, enter the user password for this application.  
  
5.  If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.  
  
### To set credentials for a user mapping from the client utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient -setcredentials \<application name>**, where **\<application name>** is the name of the affiliate application you want to remove the user mapping for.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Create User Mappings](../core/how-to-create-user-mappings.md)   
 [SSO Mappings](../core/sso-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)