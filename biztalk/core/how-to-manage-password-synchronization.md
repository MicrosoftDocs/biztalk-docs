---
description: "Learn more about: How to Manage Password Synchronization"
title: "How to Manage Password Synchronization"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Manage Password Synchronization
Use the MMC Snap-in or the SSOMANAGE command line utility to enable or disable SSO features, and to display current SSO database settings.  
  
### To manage features or display settings using the MMC Snap-In  
  
1.  Right-click the appropriate feature or database.  
  
2.  Click the appropriate menu item.  
  
### To enable SSO features using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -enable** and press Enter.  
  
### To disable SSO features using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -disable** and press Enter.  
  
### To display current database settings using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -displaydb** and press Enter.  
  
## See Also  
 [Password Synchronization](../core/password-synchronization2.md)
