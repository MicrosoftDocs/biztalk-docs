---
description: "Learn more about: How to Recover the BAM Portal"
title: "How to Recover the BAM Portal"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Recover the BAM Portal
If you are using Business Activity Monitoring (BAM), you must recover the BAM portal as a part of recovering your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. If you are not using BAM, this procedure is optional.  
  
 The procedure for recovering the BAM portal configuration differs considerably depending on which version of IIS you are using. When you restore the configuration for IIS 7, you use **Appcmd.exe**, and you restore the configuration for the entire default Web site, not just the BAM portal.  
  
## Prerequisites  
 You must be logged on as a member of the Administrators group to perform this procedure.  
  
### To recover the BAM portal configuration (IIS 7.0)  
  
1.  On the Run dialog, in the Open box, type the following: `runas /user:`*computername*`\`*accountname* `cmd`, and then click **OK** or press **Enter**.  
  
     *Accountname* must be a member of the administrators group on the local computer.  
  
2.  When prompted, type the password for *accountname*, and then press **Enter**.  
  
3.  Type `cd %windir%\system32\inetsrv`, and then press **Enter**.  
  
4.  Type `appcmd restore backup “`*backupname*`”`, and then press **Enter**.  
  
     *Backupname* is the name of a backup you previously created using **Appcmd.exe**. This backup must exist in the **%windir%\system32\inetsrv\backup** directory. The backup cannot be used to restore passwords created on a different computer. If the BAMAppPool is configured to run under an identity other than the default **NetworkService** account, you must configure the account and password separately, as described in the next step.  
  
5.  Using the **Internet Information Services (IIS) Manager**, select **Application Pools** in the **Connections** pane.  
  
6.  In the **Application Pools** pane, right-click the **BAMAppPool**, then click **Advanced Settings**  
  
7.  In the **Advanced Setting**s dialog, scroll down to the **Process Model** section. Click the **Identity** box. This will cause an ellipses button to appear on the right side of the box. Click the **ellipses** button.  
  
8.  In the **Application Pool Identity** dialog, click the **Custom account** button, then click the **Set** button.  
  
9. In the **Set Credentials** dialog box, enter the account name and password you want to use for the BAMAppPool. The account name should be entered as *computer name*`\`*accountname*, or *domain*`\`*accountname*. Click **OK** to close the **Set Credentials** dialog.  
  
10. Click **OK** to close the **Application Pool Identity** dialog.  
  
11. Click **OK** to close the **Advanced Settings** dialog.  
  
12. Verify that the **BAMAppPool** is selected in the list of application pools. In the **Actions** pane on the right of the **Internet Information Services (IIS) Manager** screen, under **Application Pool Tasks**, click **Start**.  
  
## See Also  
 [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [BAM Portal](../core/bam-portal.md)
