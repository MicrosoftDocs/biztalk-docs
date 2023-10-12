---
description: "Learn more about: How to Set the Enterprise Single Sign-On Server"
title: "How to Set the Enterprise Single Sign-On Server"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Set the Enterprise Single Sign-On Server
Every time that you use the command line management utility, ssomanage, you must first point the user to the Single Sign-On (SSO) server that you want to connect to.  
  
 You can do this in one of two ways:  
  
-   Individual users can point themselves to the correct Single Sign-On server.  
  
-   A local computer administrator for the Single Sign-On server can point all the members of the Single Sign-On Users account to this server.  
  
### To set the Enterprise Single Sign-On server using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and then click **Select**.  
  
3.  Browse to the desired server.  
  
4.  If appropriate, select the **Set SSO Server for all users** check box.  
  
5.  Click **OK**.  
  
### To set the Enterprise Single Sign-On server for a single user  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –server <Single Sign-On Server>`, where *\<Single Sign-On Server>* is the computer name of the Single Sign-On server that the user wants to connect to.  
  
### To set the Enterprise Single Sign-On server for all users  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –serverall <Single Sign-On Server>`, where *\<Single Sign-On Server>* is the computer name of the Single Sign-On server that all members of the Single Sign-On Users account will be pointed to.  
  
### To determine the Enterprise Single Sign-On Server to which a user is connected  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –showserver`.  
  
> [!NOTE]
>  This command displays the settings for the current user and also for other users if they exist.  
  
## See Also  
 [How to Enable Enterprise Single Sign-On](../esso/how-to-enable-enterprise-single-sign-on.md)   
 [How to Disable Enterprise Single Sign-On](../esso/how-to-disable-enterprise-single-sign-on.md)   
 [How to Display the Credential Database Information](../esso/how-to-display-the-credential-database-information.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)
