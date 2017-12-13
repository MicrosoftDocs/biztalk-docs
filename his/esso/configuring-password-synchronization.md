---
title: "Configuring Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f39b5efd-2e6d-4d33-b025-a98d0d5c6ced
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Password Synchronization
Use the SSOCONFIG command-line utility to configure your password synchronization settings. You can use this tool to specify directories for replay files and also change maximum password synchronization age.  
  
### To specify the directory for replay files  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoconfig -replayfiles <replay files directory> | -default`and press ENTER.  
  
## Note   Replay files are not deleted when you change the service account. If you change this account, you must delete the replay files manually.  
  
#### To display or change maximum password synchronization age  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoconfig -syncage <maximum password age in hours>` and press ENTER.  
  
> [!NOTE]
>  The SSOCONFIG utility uses the time on the computer that is running SQL Server as its system time. Remember this when you are using any commands related to time.  
  
## See Also  
 [Password Synchronization](../esso/password-synchronization3.md)