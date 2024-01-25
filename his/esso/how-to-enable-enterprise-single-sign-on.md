---
description: "Learn more about: How to Enable Enterprise Single Sign-On"
title: "How to Enable Enterprise Single Sign-On"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Enable Enterprise Single Sign-On
The enabling command enables the entire Enterprise Single Sign-On (SSO) system. After you run the enabling command, there is a short delay before all Single Sign-On servers are enabled, because each server polls the Credential database for the latest global information.  
  
 If you want to configure affiliate applications and mappings in the SSO system, you must also create an affiliate application. After an SSO affiliate administrator creates an affiliate application, an application administrator can make changes to it, and application users (end users) can create their own mappings. For more information, see [Managing Affiliate Applications](../esso/managing-affiliate-applications.md) and [Managing User Mappings](../esso/managing-user-mappings.md).  
  
### To enable the SSO system using the MMC Snap-In  
  
1.  Click **Start**, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Enable**.  
  
### To enable the SSO system using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –enablesso`.  
  
### To enable SSO to create affiliate applications and mappings  
  
1.  Log on as an SSO administrator or SSO affiliate administrator to the SSO Server, or on a computer that has the SSO administration sub services of SSO.  
  
2.  Click **Start**, click **Run**, and then type `cmd`.  
  
3.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type `ssomanage -enablesso` to enable the Enterprise Single Sign-On service.  
  
5.  Log on as an SSO affiliate administrator.  
  
6.  Type `ssomanage -createapps <application file>` to create an affiliate application, where *\<application file>* is the XML file that contains definitions for the affiliate applications.  
  
## See Also  
 [How to Set the Enterprise Single Sign-On Server](../esso/how-to-set-the-enterprise-single-sign-on-server.md)   
 [How to Disable Enterprise Single Sign-On](../esso/how-to-disable-enterprise-single-sign-on.md)   
 [How to Update the Credential Database](../esso/how-to-update-the-credential-database.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)
