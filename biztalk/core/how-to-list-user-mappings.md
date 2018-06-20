---
title: "How to List User Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [SSO maps], listing maps"
  - "maps [SSO], listing maps"
ms.assetid: f9b73785-3a59-45c8-9e88-d2d16b5a46aa
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to List User Mappings
Use this command to list all the existing mappings for the specified user.  
  
 You must be an SSO administrator, application administrator, SSO affiliate administrator, or user to do this task.  
  
 Enabled user mappings appear as (E) \<*domain*\>\\*\<username\>*, while disabled user mappings appear as (D) \<*domain*\>\\*\<username\>*.  
  
### To list user mappings using the administration utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Do one of the following:  
  
   - Type **ssomanage –listmappings *\<domain\>\\<username\>*** to list all the mappings a given user has in the affiliate applications he/she belongs to, where *\<domain\>* is the Microsoft Windows domain for the user account, and *\<username\>* is the Windows user name for which you want to list the user mappings. If the user is an Affiliate Administrator or an SSO Administrator, this command will list all the mappings for that user in all the affiliate applications.  
  
      Or  
  
   - Type **ssomanage –listmappings *\<application name\>*** to list all the user mappings for a given application.  
  
      Or  
  
   - If you are an application administrator, type **ssomanage –listmappings *\<domain\>\\<username\>* *\<application name\>*** to list all the mappings a given user has in the affiliate applications for which you are an administrator.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To list user mappings using the client utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient –listmappings** to list all the mappings you have.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Create User Mappings](../core/how-to-create-user-mappings.md)   
 [SSO Mappings](../core/sso-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)