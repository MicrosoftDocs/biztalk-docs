---
title: "How to Generate the Master Secret | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 539b4def-d35c-4888-9e94-9a86f4a5f375
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Generate the Master Secret
You must have administrator rights on the master secret server in order to generate the master secret. In addition, you must perform this task from the master secret server.  
  
 The first server where you install Enterprise Single Sign-On (SSO) becomes the master secret server.  
  
> [!IMPORTANT]
>  There can be only one master secret server in your SSO system.  
> 
> [!NOTE]
>  When Enterprise Single Sign-On is installed as part of the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] installation, the master secret is generated as part of the Configuration Wizard. You only need to perform this task if you want to generate a new master secret.  
  
### To generate the master secret using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Generate Master Secret**.  
  
### To generate the master secret using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoconfig –generatesecret <backup file>`, where \<*backup file*> is the name of the file that contains the master secret.  
  
     You will be prompted to enter a password to protect the file you just created.  
  
## See Also  
 [How to Back Up the Master Secret](../esso/how-to-back-up-the-master-secret.md)   
 [Master Secret Server](../esso/master-secret-server.md)   
 [Managing the Master Secret](../esso/managing-the-master-secret.md)