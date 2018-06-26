---
title: "How to Generate the Master Secret | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Master Secret server, generating"
  - "managing [Master Secret server], generating"
ms.assetid: 5512a8ee-bc5b-4fe4-90c7-41e3baaa723b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Generate the Master Secret
You must have administrator rights on the master secret server in order to perform this task. In addition, you must perform this task from the master secret server.  
  
 The first server where you install Enterprise Single Sign-On becomes the master secret server.  
  
> [!IMPORTANT]
>  There can be only one master secret server in your SSO system.  
> 
> [!NOTE]
>  When Enterprise Single Sign-On is installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation, the master secret is generated as part of the Configuration Wizard. You will only need to perform this task if you want to generate a new master secret.  
  
### To generate the master secret using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Generate Secret**.  
  
### To generate the master secret using the command line  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoconfig –generateSecret \<*backup file*\>**, where \<*backup file*\> is the name of the file that contains the master secret.  
  
     You will be prompted to enter a password to protect the file you just created.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md)   
 [Master Secret Server](../core/master-secret-server.md)   
 [Managing the Master Secret](../core/managing-the-master-secret.md)