---
title: "How to Back Up the Master Secret | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0841c52a-7b15-45f8-9900-f5c9e3abd90b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Back Up the Master Secret
You can back up the master secret from the master secret server onto an NTFS file system or removable media, such as a floppy disk.  
  
 You must be a Single Sign-On administrator and a Windows administrator to perform this task. The Single Sign-On (SSO) system will prompt you for a password. To restore the secret later, you must specify the same password.  
  
> [!CAUTION]
>  If the master secret server crashes and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the Credential database. You must back up the master secret, or you risk losing data from the Credential database.  
  
### To back up the master secret using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Back up Master Secret**.  
  
### To back up the master secret using the command line  
  
1.  On the **Start** menu, click **Programs**, and then click **Accessories**. Right-click **Command Prompt**, and then click **Run As…**.  
  
2.  Select the appropriate Administrator, and then click **OK**.  
  
3.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type `ssoconfig –backupsecret <backup file>`, where *\<backup file>* is the path and name of the file where the master secret will be backed up, for example, `A:\ssobackup.bak`.  
  
5.  Provide a password to help protect this file.  
  
     You will be prompted to confirm the password and to provide a password hint to help you remember this password.  
  
> [!IMPORTANT]
>  You must save and store the backup file in a secure location.  
  
## See Also  
 [How to Generate the Master Secret](../esso/how-to-generate-the-master-secret.md)   
 [How to Restore the Master Secret](../esso/how-to-restore-the-master-secret.md)   
 [Master Secret Server](../esso/master-secret-server.md)   
 [Managing the Master Secret](../esso/managing-the-master-secret.md)