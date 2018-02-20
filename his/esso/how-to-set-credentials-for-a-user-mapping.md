---
title: "How to Set Credentials for a User Mapping | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42fddcba-5b91-4dac-95f4-8288bed3f90f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Set Credentials for a User Mapping
Use the **setcredentials** command to set the credentials for a user to access a specific application.  
  
 This command does not display the password as you type it.  
  
 If the user mapping already exists, this command sets the credentials for the existing mapping. If you have not created the user mapping, the SSO system prompts you for the user ID for the application.  
  
### To set credentials for an user mapping  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –setcredentials <domain>\<username> <applicationname>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name, and *\<applicationname>* is the specific application for which you want to set the credentials.  
  
4.  When the SSO system prompts you for the user credentials, enter the user password for this application.  
  
5.  If you have not created the user mapping, the SSO system prompts you for the user ID for the application.  
  
### To set credentials for a user mapping from client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient -setcredentials <application name>`,where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.  
  
## See Also  
 [How to Create User Mappings](../esso/how-to-create-user-mappings.md)   
 [SSO Mappings](../esso/sso-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)