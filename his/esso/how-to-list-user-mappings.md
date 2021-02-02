---
description: "Learn more about: How to List User Mappings"
title: "How to List User Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0af0932-c1e6-4663-897b-e86549ed1acb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to List User Mappings
Use the **listmappings** command to list all the existing mappings for the specified user. You must be a Single Sign-On (SSO) Administrator, Application Administrator, SSO Affiliate Administrator, or user to do this task.  
  
 Enabled user mappings appear as (E) *\<domain>\\<username\>*, whereas disabled user mappings appear as (D) *\<domain>\\<username\>*.  
  
### To list user mappings using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  To list all the mappings that a given user has in the affiliate applications that the user belongs to, type:  
  
     `ssomanage –listmappings <domain>\<username>`  
  
     where *\<domain>* is the Windows domain for the user account, and *\<username>* is the Windows user name for which you want to list the user mappings. If the user is an Affiliate Administrator or an SSO Administrator, this command lists all the mappings for that user in all the affiliate applications.  
  
     Or  
  
4.  To list all the user mappings for a given application, type `ssomanage –listmappings <application name>`.  
  
     Or  
  
5.  If you are an application administrator, and you want to list all the mappings a given user has in the affiliate applications for which you are an administrator, type `ssomanage –listmappings <domain>\<username> <application name>`.  
  
### To list user mappings using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –listmappings` to list all the mappings you have.  
  
## See Also  
 [How to Create User Mappings](../esso/how-to-create-user-mappings.md)   
 [SSO Mappings](../esso/sso-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)
