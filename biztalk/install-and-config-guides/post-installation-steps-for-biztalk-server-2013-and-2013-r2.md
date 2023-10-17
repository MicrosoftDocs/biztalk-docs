---
description: "Learn more about: Post-installation Steps for BizTalk Server 2013 and 2013 R2"
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

    - Right-click the protocol, and then click **Enable**.
    - Repeat to enable the other protocol if necessary.
    - In the left-hand pane, click **SQL Server Services**.
    - In the right-hand pane, right-click **SQL Server (MSSQLSERVER)**, and click **Stop**.
    - When the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and click **Start**.

    > [!IMPORTANT]
    >  If you are using [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], the **NS$BAMAlerts** service may be stopped. Restart the service.

4. Close the **Configuration Manager**.

##  <a name="BKMK_DTC"></a> Enable DTC on the Local Host Server

1. Open Component Services:

    - **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Select the Windows button, and type **Component Services**. In the Results window, select **Component Services**.

    - **Windows 8.1**: Select the Windows button, and type **Administrative Tools**. In the Search window, select **Settings**. In the Results window, click **Administrative Tools**. Double-click **Component Services**.

    - **Windows 7 SP1**: Select **Start**. In the **Search** text box, type **Component Services**, and click it to open.

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

    - **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Click the Windows button, and type **Windows Firewall**. In the Results window, click **Windows Firewall**.

    - **Windows 8.1**: Click the Windows button, and type **Windows Firewall**. In the Search window, click **Settings**. In the Results window, click **Windows Firewall**.

    - **Windows 7 SP1**: Click **Start**. In the **Search** text box, type **Windows Firewall**, and click it to open.

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

- **Backup BizTalk Server**: This SQL Agent job backs up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the log files. When configuring the job, you determine parameters like frequency and file location.

  The following links describe the SQL Agent job and its parameters:

  - [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)
  - [Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)

  This SQL Agent job also truncates the transaction logs, which helps improve performance. The **Backup BizTalk Server** job may not remove or delete backup files, including older files.

- **DTA Purge and Archive**: This SQL Agent job truncates and archives the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Tracking database (BizTalkDTADb). When configuring the job, you determine parameters like how many days to keep completed instances and how many to days to keep all data.

  The following links describe the SQL Agent job and its parameters:

  - [Archive and Purge the BizTalkDTADb Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)
  - [Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md)

  This SQL Agent job directly impacts performance by maintaining the Tracking host and purging tracking events. Performance topics include:

  - [How to maintain and troubleshoot BizTalk Server databases](/troubleshoot/developer/biztalk/management-operations/maintain-troubleshoot-database)
  - [Tracking Database Sizing Guidelines](../core/tracking-database-sizing-guidelines.md)

- When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed, several SQL Agent jobs are automatically created, as described in the following links:

  - [Description of the SQL Server Agent jobs in BizTalk Server](/troubleshoot/developer/biztalk/setup-config/sql-server-agent-jobs-biztalk)

  - [Database Structure and Jobs](../core/database-structure-and-jobs.md)

##  <a name="BKMK_InstallCU"></a> Install Cumulative Updates

After you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], install any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cumulative updates listed in Windows Update. For more information, go to [Service Pack and cumulative update list for BizTalk Server](https://support.microsoft.com/topic/service-pack-and-cumulative-update-list-for-biztalk-server-108e5e94-4558-8b57-d5fb-45984506d56f).

## Next
[Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)

## See Also
 [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md)

[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)

[Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md)

[Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md)

[Uninstall and unconfigure BizTalk Server to remove it](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)
