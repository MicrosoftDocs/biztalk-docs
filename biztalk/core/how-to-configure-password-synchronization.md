---
description: "Learn more about: How to Configure Password Synchronization"
title: "How to Configure Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Password Synchronization [SSO], replay files"
  - "Password Synchronization [SSO], maximum age"
  - "SSOCONFIG command line utility"
  - "Password Synchronization [SSO], SSOCONFIG command line utility"
  - "Password Synchronization [SSO], configuring"
  - "configuring, Password Synchronization [SSO]"
ms.assetid: 04000dfc-02b9-4d50-babe-8bc8a07a33b7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Password Synchronization
Use the SSOCONFIG command line utility to configure your password synchronization settings.  
  
### To specify the directory for replay files  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig -replayfiles \<replay files directory\> &#124; -default** and press Enter.  
  
> [!NOTE]
>  Replay files are not deleted when you change the service account. If you change this account, you will need to delete the replay files manually.  
  
#### To display or change maximum password synchronization age  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig -syncage \<maximum password age in hours\>** and press Enter.  
  
> [!NOTE]
>  The SSOCONFIG utility uses the time on the SQL Server computer as its system time. Remember this when using any commands related to time.  
  
## See Also  
 [Password Synchronization](../core/password-synchronization2.md)
