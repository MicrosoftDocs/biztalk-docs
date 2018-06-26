---
title: "How to Delete an Affiliate Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications [SSO], deleting"
  - "managing [SSO applications], deleting"
  - "deleting, applications [SSO]"
ms.assetid: c7ec065e-ef10-49ff-a350-105dd08dc4a9
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete an Affiliate Application
You can use the MMC Snap-In or the command line to delete the specified affiliate application from the SSO database.  
  
> [!IMPORTANT]
>  When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.  
  
> [!IMPORTANT]
>  You must be an SSO administrator or SSO affiliate administrator to perform this task.  
  
### To delete an affiliate application using the MMC Snap-In  
  
1.  On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click the affiliate application, and then click **Delete**.  
  
### To delete an affiliate application using the command line  
  
1. On the **Start** menu, click **run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –deleteapp *\<application name\>**<em>, where *\<application name\></em> is the name of the affiliate application you want to remove from the SSO database.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)