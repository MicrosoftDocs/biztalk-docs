---
description: "Learn more about: How to Restore the Master Secret"
title: "How to Restore the Master Secret | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b331c9c5-ca90-4a05-b3f6-59db88bf73dc
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Restore the Master Secret
As part of data recovery procedures, you might have to restore the master secret to reuse existing data. To perform this task, you must log on to the master secret server by using an account that is both a Windows administrator and a Single Sign-On (SSO) administrator.  
  
### To restore the master secret using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Restore Master Secret**.  
  
### To restore the master secret using the command line  
  
1.  On the **Start** menu, click **Programs**, and then click **Accessories**. Right-click **Command Prompt**, and then click **Run As…**.  
  
2.  Select the appropriate Administrator, and then click **OK**.  
  
3.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type `ssoconfig –restoresecret <restore file>`, where *\<restore file>* is the path and name of the file where the master secret is stored.  
  
## See Also  
 [How to Generate the Master Secret](../esso/how-to-generate-the-master-secret.md)   
 [How to Back Up the Master Secret](../esso/how-to-back-up-the-master-secret.md)   
 [Master Secret Server](../esso/master-secret-server.md)   
 [Managing the Master Secret](../esso/managing-the-master-secret.md)
