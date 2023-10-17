---
description: "Learn more about: How to Disable a User Mapping"
title: "How to Disable a User Mapping | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51c745dd-4d39-46e5-88bf-b803ae2e0a1b
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Disable a User Mapping
You can disable a user mapping when you want to turn off all operations associated with a given mapping. You must disable a user mapping before you can remove it.  
  
 When you disable a user mapping, it will appear as (D) *\<domain>\\<username\>* when you list the user mappings.  
  
### To disable a user mapping using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press **ENTER**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –disablemapping <domain>\<username><application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name for which you want to disable the credentials, and *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.  
  
### To disable a user mapping using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press **ENTER**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –disablemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.  
  
## See Also  
 [SSO Mappings](../esso/sso-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)
