---
description: "Learn more about: How to Enable a User Mapping"
title: "How to Enable a User Mapping"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Enable a User Mapping
You must enable a user mapping before it you can use the mapping in the Single Sign-On (SSO) system.  
  
 When you enable a user mapping, it appears as (E) *\<domain>\\<username\>* when you list the user mappings.  
  
### To enable a user mapping using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –enablemapping <domain>\<username> <application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name for which you want to enable the credentials, and *\<application name>* is the name of the affiliate application for which you want to remove the user mapping, and then press ENTER.  
  
### To enable a user mapping using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –enablemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.  
  
## See Also  
 [How to Create User Mappings](../esso/how-to-create-user-mappings.md)   
 [SSO Mappings](../esso/sso-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)
