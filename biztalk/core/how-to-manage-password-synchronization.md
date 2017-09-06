---
title: "How to Manage Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Password Synchronization [SSO], managing"
  - "managing [SSO], disabling features"
  - "managing [SSO], enabling features"
  - "Password Synchronization [SSO], SSOMANAGE command line utility"
  - "SSO database, SSOMANAGE command line utility"
  - "managing, Password Synchronization [SSO]"
  - "SSO database, database settings"
  - "SSOMANAGE command line utility"
ms.assetid: 033e63f2-e5b0-4400-99c3-145679d9b84e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manage Password Synchronization
Use the MMC Snap-in or the SSOMANAGE command line utility to enable or disable SSO features, and to display current SSO database settings.  
  
### To manage features or display settings using the MMC Snap-In  
  
1.  Right-click the appropriate feature or database.  
  
2.  Click the appropriate menu item.  
  
### To enable SSO features using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -enable** and press Enter.  
  
### To disable SSO features using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -disable** and press Enter.  
  
### To display current database settings using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -displaydb** and press Enter.  
  
## See Also  
 [Password Synchronization](../core/password-synchronization2.md)