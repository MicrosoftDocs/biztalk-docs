---
title: "How to List Affiliate Applications | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 064a26e0-082b-40a4-a254-3a10f213fe65
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to List Affiliate Applications
Use the **listapps** command to list all the affiliate applications. If the user is a member of the Application Administrators account, this command only displays the application for which the user is an administrator.  
  
### To list affiliate applications using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On (SSO) installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -listapps [all]` where *all* is an optional parameter that will also display applications using the Configuration Store feature.  
  
     If the user who runs this command is an Application administrator, it only lists the applications for which that user is an administrator. If the user who runs this command is an Affiliate Administrator or an SSO Administrator, it lists all the affiliate applications.  
  
### To list affiliate applications using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –listapps` to list the affiliate applications.  
  
     This lists only the affiliate applications that the user who is performing this task is a member of. That is, the user must belong to the application user group account for that affiliate application.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [How to Create an Affiliate Application](../esso/how-to-create-an-affiliate-application.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)