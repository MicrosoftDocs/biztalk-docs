---
description: "Learn more about: How to List Affiliate Applications"
title: "How to List Affiliate Applications"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to List Affiliate Applications
Use this command to list all the affiliate applications. If the user is a member of the Application Administrators account, this command will only display the application for which the user is an administrator.  
  
### To list affiliate applications using the administration utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage -listapps [all]** where **all** is an optional parameter that will also display applications using the Configuration Store feature. If the user running this command is an Application administrator, it will only list the applications for which they are an administrator. If the user running this command is an Affiliate Administrator or an SSO Administrator, it will list all the affiliate applications.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To list affiliate applications using the client utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient –listapps** to list the affiliate applications. This will list only the affiliate applications that the user performing this task is a member of, i.e., they need to belong the application user group account for that affiliate application.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [How to Create an Affiliate Application](../core/how-to-create-an-affiliate-application.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)
