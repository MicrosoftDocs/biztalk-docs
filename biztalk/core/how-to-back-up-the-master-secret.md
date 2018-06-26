---
title: "How to Back Up the Master Secret | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [Master Secret server], backing up"
  - "backing up, Master Secret server"
  - "Master Secret server, backing up"
ms.assetid: 22c23f66-b7df-4379-8a9f-065406ba8aa8
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Back Up the Master Secret
You can back up the master secret from the master secret server onto an NTFS file system or removable media, such as a floppy disk.  
  
 You must be a Single Sign-On Administrator and a Windows administrator to perform this task. The SSO system will prompt you for a password. To restore the secret later, you must specify the same password.  
  
> [!CAUTION]
>  If the master secret server fails and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the SSO database. You must back up the master secret, or you risk losing data from the SSO database.  
  
### To back up the master secret using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Backup Secret**.  
  
### To back up the master secret using the command line  
  
1. On the **Start** menu, click **All Programs**, and then click **Accessories**. Right-click **Command Prompt**, and then click **Run As…**.  
  
2. Select the appropriate Administrator, and then click **OK**.  
  
3. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4. Type **ssoconfig –backupSecret *\<backup file\>**<em>, where *\<backup file\></em> is the path and name of the file where the master secret will be backed up. For example, A:\ssobackup.bak  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
5. Provide a password to protect this file. You will be prompted to confirm the password and to provide a password hint to help you remember this password.  
  
> [!IMPORTANT]
>  You must save and store the backup file in a secure location.  
  
## See Also  
 [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)   
 [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md)   
 [Master Secret Server](../core/master-secret-server.md)   
 [Managing the Master Secret](../core/managing-the-master-secret.md)