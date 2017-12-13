---
title: "Managing Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f27eb2b-0ab3-40de-ae6f-741b98f31ce9
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Password Synchronization
Use the SSOMANAGE command-line utility to enable or disable Single Sign-On (SSO) features, and to display current SSO database settings.  
  
### To manage features or display settings using the MMC Snap-In  
  
1.  Right-click the appropriate feature or database.  
  
2.  Click the appropriate command.  
  
### To enable SSO features using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -enable` and press ENTER.  
  
### To disable SSO features using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -disable` and press ENTER.  
  
### To display current database settings using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -displaydb` and press ENTER.  
  
## See Also  
 [Password Synchronization](../esso/password-synchronization3.md)