---
title: "How to Create User Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps [SSO], creating"
  - "managing [SSO maps], creating user maps"
ms.assetid: c2e9f0db-920b-4d89-8e1e-5dc92805fd23
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create User Mappings
Use this command to create one or more user mappings, as specified in the XML file. The following is an example XML file.  
  
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
  
 If a user account is changed, you must use this command to create a mapping for the new user account. You should also remove the old user mapping. For more information about removing a mapping, see [How to Delete User Mappings](../core/how-to-delete-user-mappings.md).  
  
 After you create a user mapping, you must enable it before you can use this mapping in the SSO system. For more information, see [How to Enable a User Mapping](../core/how-to-enable-a-user-mapping.md).  
  
> [!IMPORTANT]
>  Only domain groups are supported for user mappings.  
  
### To create user mappings using the administration utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –createmappings *\<mappings file name\>**<em>, where *\<mappings file name\></em> is the name of file that contains the user mapping(s) you want to create.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To create user mappings using the client utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssoclient –setcredentials *\<application name \>**<em>, where *\<application name \></em> is the name of affiliate application that the user wants to create a mapping for.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Mappings](../core/sso-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)