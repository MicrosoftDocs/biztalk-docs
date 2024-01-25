---
description: "Learn more about: How to Disable a User Mapping"
title: "How to Disable a User Mapping"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Disable a User Mapping
You can disable a user mapping when you want to turn off all operations associated with a given mapping. You must disable a user mapping before you can remove it.  
  
 When you disable a user mapping, it will appear as (D) *\<domain\>\\<username\>* when you list the user mappings.  
  
## Disable a user mapping using the administration utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –disablemapping \<_domain_\>\\<_username_\> \<_application name_\>**, where \<*domain*\> is the Windows domain for the user account, and *\<username\>* is the Windows user name for which you want to disable the credentials, and *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## Disable a user mapping using the client utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssoclient –disablemapping \<*application name*\>**, where \<*application name*\> is the name of the affiliate application you want to remove the user mapping for.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Mappings](../core/sso-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)
