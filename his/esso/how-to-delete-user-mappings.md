---
description: "Learn more about: How to Delete User Mappings"
title: "How to Delete User Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82c4cdff-b82d-4cfd-8e20-220a2fe78656
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Delete User Mappings
Use these commands to delete one or more user mappings, as specified in the XML file. The following is an example XML file.  
  
```  
<sso>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name1</externalApplication>   
<externalUserId>App1UserName</externalUserId>   
</mapping>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name2</externalApplication>   
<externalUserId>App2UserName</externalUserId>   
</mapping>  
</sso>  
```  
  
 If a user is not a member of the Application Users account, or does not exist in Active Directory, you should use this command to remove the user mapping from the Credential database.  
  
 If a user account is changed, you must use this command to remove the old user mapping, and then create a new user mapping for the new user account. For more information about creating a mapping, see [How to Create User Mappings](../esso/how-to-create-user-mappings.md).  
  
### To delete user mappings using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –deletemappings <mappings file name>`, where \<*mappings file name*> is the name of the file that contains the user mappings that you want to delete.  
  
### To delete a specific user mapping using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –deletemapping <domain>\<username> <application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name, and \<*application name*> is the specific application for which you want to remove the user mapping.  
  
### To delete a user mapping using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –deletemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.  
  
## See Also  
 [SSO Mappings](../esso/sso-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)
