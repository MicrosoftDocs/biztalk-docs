---
description: "Learn more about: How to Delete an Affiliate Application"
title: "How to Delete an Affiliate Application"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Delete an Affiliate Application
Use the MMC Snap-In or the **deleteapps** command to delete the specified affiliate application from the Credential database.  
  
> [!IMPORTANT]
>  When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.  
  
> [!IMPORTANT]
>  You must be an SSO administrator or SSO affiliate administrator to perform this task.  
  
### To delete an affiliate application using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click the affiliate application, and then click **Delete**.  
  
### To delete an affiliate application using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –deleteapp <application name>`, where *\<application name>* is the name of the affiliate application you want to remove from the Credential database.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)
