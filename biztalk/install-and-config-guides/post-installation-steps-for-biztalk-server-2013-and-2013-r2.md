---
title: "Post-installation Steps for BizTalk Server 2013 and 2013 R2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3b47843-9da5-4144-8b84-135494b8ab43
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Post-installation Steps for BizTalk Server 2013 and 2013 R2
  
##  <a name="BKMK_NamedPipes"></a> Enable TCP/IP and Named Pipes  
  
1. Open **SQL Server Configuration Manager**.  
  
2. Expand **SQL Server Network Configuration**, and select **Protocols for MSSQLSERVER**.  
  
3. Verify that both **TCP/IP** and **Named Pipes** are enabled. If enabled, proceed to the next step.  
  
    If not enabled:  
  
   -   Right-click the protocol, and then click **Enable**.  
  
   -   Repeat to enable the other protocol if necessary.  
  
   -   In the left-hand pane, click **SQL Server Services**.  
  
   -   In the right-hand pane, right-click **SQL Server (MSSQLSERVER)**, and click **Stop**.  
  
   -   When the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and click **Start**.  
  
   > [!IMPORTANT]
   >  If you are using [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], the **NS$BAMAlerts** service may be stopped. Restart the service.  
  
4. Close the **Configuration Manager**.  
  
##  <a name="BKMK_DTC"></a> Enable DTC on the Local Host Server  
  
1. Open Component Services:  
  
    **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Select the Windows button, and type **Component Services**. In the Results window, select **Component Services**.  
  
    **Windows 8.1**: Select the Windows button, and type **Administrative Tools**. In the Search window, select **Settings**. In the Results window, click **Administrative Tools**. Double-click **Component Services**.  
  
    **Windows 7 SP1**: Select **Start**. In the **Search** text box, type **Component Services**, and click it to open.  
  
2. In the console tree, expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, and then click **Local DTC**.  
  
3. Right-click **Local DTC** and select **Properties** to open the **Local DTC Properties**.  
  
4. Select the **Security** tab.  
  
5. Confirm the following options are checked:  
  
   - **Network DTC Access**  
  
   - **Allow Inbound**  
  
   - **Allow Outbound**  
  
   - **No Authentication Required**  
  
     For additional settings that may be needed, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).  
  
6. Select **OK** to close the **Local DTC Properties** dialog box. Restart the MSDTC service if prompted.  
  
7. Close **Component Services**.  
  
##  <a name="BKMK_Firewall"></a> Configure Windows Firewall to Enable DTC  
  
1. Open **Windows Firewall**:  
  
    **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Click the Windows button, and type **Windows Firewall**. In the Results window, click **Windows Firewall**.  
  
    **Windows 8.1**: Click the Windows button, and type **Windows Firewall**. In the Search window, click **Settings**. In the Results window, click **Windows Firewall**.  
  
    **Windows 7 SP1**: Click **Start**. In the **Search** text box, type **Windows Firewall**, and click it to open.  
  
2. Click **Advanced Settings** and click **Inbound Rules**.  
  
3. In the **Inbound Rules** pane, right-click **Distributed Transaction Coordinator** \* (as appropriate), and then click **Enable Rule**.  
  
4. Click **Outbound Rules**.  
  
5. In the **Outbound Rules** pane, right-click **Distributed Transaction Coordinator** \* (as appropriate), and then click **Enable Rule**.  
  
6. On the **Control Panel**, change the view to list by icons, and then double-click **Administrative Tools**.  
  
7. Double-click **Services**.  
  
8. Right-click **COM+ System Application**, click **Restart**, and wait for the service to restart.  
  
9. Right-click and restart the **Distributed Transaction Coordinator** service.  
  
10. Right-click and restart the **SQL Server (MSSQLSERVER)** service.  
  
11. Close **Services (Local)**, and then close **Administrative Tools**.  
  
##  <a name="BKMK_SQLAgent"></a> Configure SQL Agent Jobs  
  
|            Job            |                                                                                                                                                                                                                                                                                                                     Description                                                                                                                                                                                                                                                                                                                     |                                                                                                                                                                                                 Why configure                                                                                                                                                                                                  |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Backup BizTalk Server** |                                     This SQL Agent job backs up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the log files. When configuring the job, you determine parameters like frequency and file location.<br /><br /> The following links describe the SQL Agent job and its parameters:<br /><br /> [Backing Up and Restoring BizTalk Server Databases](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)<br /><br /> [How to Configure the Backup BizTalk Server Job](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)                                      | This SQL Agent job also truncates the transaction logs, which helps improve performance.<br /><br /> The **Backup BizTalk Server** job does not remove or delete backup files, including older files. To delete backup files, refer to [The "Backup BizTalk Server" job fails when backup files accumulate over time in the Microsoft BizTalk Server database server](http://support.microsoft.com/kb/982546). |
| **DTA Purge and Archive** | This SQL Agent job truncates and archives the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Tracking database (BizTalkDTADb). When configuring the job, you determine parameters like how many days to keep completed instances and how many to days to keep all data.<br /><br /> The following links describe the SQL Agent job and its parameters:<br /><br /> [Archiving and Purging the BizTalk Tracking Database](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)<br /><br /> [How to Configure the DTA Purge and Archive Job](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx) |              This SQL Agent job directly impacts performance by maintaining the Tracking host and purging tracking events.<br /><br /> Performance topics include:<br /><br /> [How to maintain and troubleshoot BizTalk Server databases](http://support.microsoft.com/kb/952555)<br /><br /> [Tracking Database Sizing Guidelines](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)              |
  
 **Additional**  
  
- When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed, several SQL Agent jobs are automatically created, as described in the following links:  
  
   [Description of the SQL Server Agent jobs in BizTalk Server](http://support.microsoft.com/kb/919776)  
  
   [Database Structure and Jobs](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)  
  
##  <a name="BKMK_InstallCU"></a> Install Cumulative Updates  
 After you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], install any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cumulative updates listed in Windows Update. [KB article 2555976](http://support.microsoft.com/kb/2555976) lists available service packs and cumulative updates.  
  
## Next  
[Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)
  
## See Also  
 [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md) 
 
[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)  

[Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md)  

[Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md)

[Uninstall and unconfigure BizTalk Server to remove it](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)
