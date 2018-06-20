---
title: "How to Recover Enterprise Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 845e6ff7-88a8-4ab4-b307-f9275d44600e
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Recover Enterprise Single Sign-On
Before you can recover BizTalk Server, you must first recover Enterprise Single Sign-On (SSO).  
  
## Prerequisites  
  
-   You must be logged on as a member of the Single Sign-On Administrators group and a member of the Administrators group to perform this task.  
  
-   You must have the password used during SSO configuration.  
  
-   All databases are intact on the remote server.  
  
-   The backup master secret file is intact and stored in a safe place.  
  
### To recover Enterprise Single Sign-On  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
2. In Microsoft BizTalk Server Configuration, in the console tree, click **Enterprise SSO**.  
  
3. In the details pane, select **Enable Enterprise Single Sign-On on this computer**, and then click **Join an existing SSO system**.  
  
4. In **Data stores**, enter the name of the SQL server hosting the SSO database and the name of the SSO database.  
  
5. In **Windows service**, enter the user name and password for the SSO service account that you used when you originally installed and configured BizTalk Server.  
  
   > [!NOTE]
   >  You can use a different account, but it must be a member of the Single Sign-On Administrators group.  
  
6. Click **Apply Configuration**.  
  
    A warning that no master secrets were retrieved is displayed. You can use Event Viewer to verify that the Enterprise Single Sign-On service is now started and running on the computer.  
  
7. Click **File**, and then click **Exit**.  
  
8. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
9. At the command prompt, type:  
  
     **cd Program Files\Common Files\Enterprise Single Sign-On**  
  
10. At the command prompt, type:  
  
     **ssoconfig -restoreSecret**  *\<backupfile\>*  
  
     where *\<backupfile\>* is the name of the master secret file that you backed up.  
  
     When **ssoconfig** prompts you for the backup file password, enter the password that was specified during SSO configuration. If the password is correct, **ssoconfig** displays the following message:  
  
     **The operation completed successfully**  
  
## See Also  
 [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [Configuring Enterprise SSO Using the BizTalk Server Configuration](http://msdn.microsoft.com/library/f63d1aec-a8c7-4e76-a67f-19af69e252f0)