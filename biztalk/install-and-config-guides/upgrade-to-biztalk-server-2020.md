---
description: "Learn more about: Upgrade to BizTalk Server 2020"
title: "Upgrade to BizTalk Server 2020"
ms.custom: "devx-track-javaee-webspherebiztalk-2020"
ms.prod: biztalk-server
ms.date: "12/30/2022"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Upgrade to BizTalk Server 2020

Upgrading to BizTalk Server 2020 from BizTalk Server 2016. This topic provides an overview of the BizTalk Server 2020 upgrade process, key information, and step-by-step instructions for upgrading from BizTalk Server 2016.

## Upgrade overview

- Read this entire document before you upgrade. BizTalk Server connects many disparate components, both internal and external, to your enterprise. Most real-world deployment scenarios extend much farther to include multiple servers and eventually clusters of both physical and virtual computers.

- No two BizTalk Server deployments are the same. Before you upgrade, gather information on your enterprise needs, and discuss the scope of your deployment with the IT Professionals, System Administrators, and Developers who use BizTalk Server. By studying this upgrade guide, and determining the specific needs of your enterprise, you are creating your own deployment roadmap.

- Use the BizTalk Server Best Practices Analyzer (BPA) to examine a BizTalk Server deployment, and generate a list of best practices. BPA performs configuration-level verification, by reading and reporting only, and uses the gathered data to determine whether best practices are being followed.

### Plan your upgrade

The following is a high-level view of the upgrade process. Each of the steps listed must be run in the order shown.

- Operating systems upgrade paths
- Microsoft SQL Server® upgrade paths
- Windows® SharePoint® Services upgrade
- Install Visual Studio side-by-side
- Install Microsoft Office 2019/2016 side-by-side

### Supported upgrade paths

The following table lists the supported operating systems that can be upgraded to BizTalk Server 2020. “Yes” means the BizTalk Server version running on that operating system can be upgraded. “No” means the BizTalk Server version running on that operating system cannot be upgraded. When “No”, the BizTalk environment must be recreated on a supported operating system.  [Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md) lists the supported operating systems.

| Operating Systems | BizTalk Server 2016 |
| --- | --- |
| Windows Server 2016 | Yes |
| Windows Server 2012 R2 | No |
| Windows 10 | Yes |
| Windows 8.1 | No |

The following table lists the supported SQL Server versions that can be upgraded to BizTalk Server 2020. The SQL Server hosts the databases used by BizTalk Server. “Yes” means BizTalk Server using that SQL Server version can be upgraded. “No” means BizTalk Server using that SQL Server version cannot be upgraded. When “No”, the BizTalk environment must be recreated on a supported SQL Server version. [Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md) lists the supported SQL Server versions.

> [!TIP]
> If your SQL Server version isn't supported, or isn't in the following list, then review the SQL Server upgrade documentation. The SQL upgrade covers more versions than what BizTalk supports. For example, if you're using SQL Server 2014, you may be able to upgrade to SQL Server 2016/2017/2019. Then, you can upgrade to BizTalk Server 2020. [Upgrade SQL Server](/sql/database-engine/install-windows/upgrade-sql-server) lists the SQL Server versions that can be upgraded.

| SQL Server | BizTalk Server 2016 |
| --- | --- |
| SQL Server 2016 | Yes |
| SQL Server 2014 | No |

The following table lists the supported Edition upgrade path from BizTalk Server 2016. “Yes” means the BizTalk Server 2016 edition can be upgraded to the edition. “No” means the BizTalk Server 2016 edition cannot be upgraded to the edition. When “No”, the BizTalk environment must be recreated.

| BizTalk Server 2016 | BizTalk Server 2020 Evaluation Edition | BizTalk Server 2020 Branch Edition | BizTalk Server 2020 Developer Edition | BizTalk Server 2020 Standard Edition | BizTalk Server 2020 Enterprise Edition |
| --- | --- | --- | --- | --- | --- |
| Evaluation | No | No | No | No | Yes |
| Branch | No | Yes | No | No | Yes |
| Developer | No | No | No | No | Yes |
| Standard | No | No | No | Yes | Yes |
| Enterprise | No | No | No | No | Yes |

## Before the upgrade – what you need to know

- **Permissions**: The user performing the upgrade must be a member of the following user groups or have the equivalent permissions:

  - Administrators group on the local computer
  - SQL Server System Administrators group on the SQL Server
  - BizTalk Server Administrators group
  - Single Sign-On (SSO) Administrators group

- **SSO**: The Single Sign-On Master Secret Server and the SQL Server that hosts the SSO database must be running during the upgrade.

- **Network Service Account**: Must have write access to %windir%\temp.

- **Certificates**: Back up the Windows certificates store:

- **DTC**: Enable Microsoft Distributed Transaction Coordinator (MSDTC), and then enable the Inbound/Outbound DTC rules:

  1. In Server Manager, select **Tools**, and open **Windows Firewall with Advanced Security**.
  2. Select **Inbound Rules**.
  3. In **Inbound Rules**, right-click **Distributed Transaction Coordinator** * (as appropriate), and then **Enable Rule**.
  4. In Windows Firewall with Advanced Security, select **Outbound Rules**.
  5. In **Outbound Rules**, right-click **Distributed Transaction Coordinator** * (as appropriate), and then **Enable Rule**.

  [Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md) lists the steps to enable MSDTC.

- **Custom Bindings**: User-defined custom bindings that are built with earlier versions of the .NET Framework are not available after you upgrade. To use the custom bindings, manually add the custom bindings in the .NET Framework 4.6 machine.config file.

- **Configuration Files**: Back up all custom configuration files in BizTalk Server 2016. BizTalk Server supports migration of changes only in the `btsntsvc.exe.config` and `bm.exe.config` files.

- **SQL Adapter**: The SQL Adapter is **removed** in BizTalk Server 2020. It is in deprecated state in BizTalk Server 2016 and prior versions. The BizTalk Server 2020 upgrade changes ports associated with EDI batching or ESBT exceptions to use WCF-SQL Adapter.

  > [!WARNING]
  > If you're using the old SQL adapter in your BizTalk solution, be sure you update your solution to use the SQL adapter in the BizTalk Adapter Pack **before** you upgrade. For more information on the SQL adapter in the BizTalk Adapter Pack, see [Get started with the BizTalk adapter for SQL](../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md).

- **TIBCO Enterprise Message Service Adapter**: Applicable starting `BizTalk Server 2020`, TIBCO Enterprise Message Service Adapter is supported in 64 bit host only.

### BAM

- **BAM DTS Packages**: Stop all BAM Data Transformation Services (DTS) packages. Otherwise, data may be lost or an online analytical processing (OLAP) cube may corrupt.

- **BAM DTS Packages and SSIS Catalog**: BizTalk Server 2016 deployed BAM DTS Packages to SSIS Package Store (MSDB). Starting with BizTalk Server 2020, BAM DTS Package will be deployed to SSIS Catalog (SSISDB). Create SSIS Catalog (SSISDB) on SQL Server before starting upgrade, otherwise upgrade process will not move deployed BAM DTS Packages to SSIS Catalog.

- **Disk Space**: The free disk space should be at least the size of the existing BAM databases.

- **Real-time Aggregations**: If you are using BAM real-time aggregations in your current version of BizTalk Server and are upgrading SQL Server, install or upgrade to the SQL Server Enterprise Edition. Otherwise, the upgrade fails.

- **maxTimeout value**: If you have a large BAM database, update the `maxTimeout` value for distributed transactions in your machine.config file to:

    ```xml
    <system.transactions>
       <machineSettings maxTimeout="23:59:59" />
    </system.transactions>
    ```

- **BAM tracking enabled with Tracking Profile Editor (TPE)**: After you upgrade, tracking profiles that were previously deployed are upgraded; however, their corresponding interceptor configurations are not upgraded. Any new intercepted BAM messages may still have the BizTalk Server 2016 references. To upgrade the corresponding interceptor configurations, use the Tracking Profile Editor to retrieve the profile for the activity, and then reapply the profile.

- **LiveData Workbook**: If you are using BAM in BizTalk Server 2016, after the upgrade, you must manually regenerate the LiveData Workbook. To regenerate the LiveData Workbook:

  1. Retrieve the BAM Definition by running the following command:

      `BM get-defxml MyDef.xml`
  2. Re-create the PivotTable reports by opening Microsoft Office Excel, and then selecting the BAM Add-ins. Import the *MyDef.xml* file created in step (1), and recreate the PivotTable reports. Save the new BAM Workbook as *MyNewBook.xls*.
  3. Rename the PivotTable reports by finding the PivotTable names in *MyDef.xml* under `<Caption>` in the  `<BAMDefinition>\<Extension>\<OWC>\<PivotTableView>\<PivotTable>\<PivotView>\<Label>` path. Use these names to rename your PivotTable reports in *MyNewBook.xls*.
  4. Regenerate the LiveData Workbook by running the following command:

      `BM regenerate-livedataworkbook MyNewBook.xls`

      > [!NOTE]
      > Regenerated LiveData Workbooks do not recreate the Excel artifacts (for example, charts) in the original LiveData Workbook. Manually recreate the artifacts.

- **BAM Tools pre-requisites**: SSIS installation is required on BAM Tools machine. Version of SSIS must be compatible to your SQL Server on machine where BAM Tools is configured. You can stop and disable SSIS windows service after installation of SSIS on this machine.

### Enterprise Single Sign-On (ESSO)

- **Upgrading from an earlier version of Enterprise Single Sign-on**: BizTalk Server includes an updated version of Enterprise Single Sign-On (ESSO). If you are installing this release on a computer with an earlier version of BizTalk, ESSO is automatically updated during setup. We recommend that you perform the following steps before upgrading:

  1. Verify that a current version of the Single Sign-On database (SSODB) is backed up to a secure location.
  2. Verify that the current master secret key is backed up to a secure location.
  3. Know the password to the master secret.

  Upgrade all the servers in a BizTalk group to the same release. This requirement also applies to a standalone master secret server.

- **Upgrade using the Enterprise Single Sign-On standalone setup**: Use the following steps to perform an upgrade on computers that have a standalone Enterprise Single Sign on installation, such as a dedicated master secret server.

  1. Verify that the current master secret key is backed up to a secure location.
  2. Verify that a current version of the SSODB is backed up to a secure location.
  3. Run the ESSO **Setup.exe** from the BizTalk Server 2020 installation media. The default installation folder is `\Platform\SSO`.
  4. In the **Autorun** dialog box, select **Microsoft Enterprise Single Sign-On**.
  5. In the Summary dialog box, select **Upgrade**.

### Multicomputer environment

In a multicomputer environment, upgrade the SSO master secret server computer. Then, upgrade the other BizTalk Server computers. Simultaneously upgrading the BizTalk computers in a group is not supported. Upgrade one computer at a time in the following order:

1. Single Sign-On master secret server
2. Run-time computers that are running BizTalk Server
3. Administration tools and monitoring computer
4. Development and any other remaining computers that are running BizTalk Server

**Additional**

Using the Settings Dashboard, you can extensively tweak BizTalk Server settings for performance optimization. You can also modify settings for the BizTalk Group, BizTalk Host, and BizTalk Host Instance. See [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).

### General information

- **Account names**: Use the default account names whenever possible. The BizTalk Server Setup program automatically configures installed components to use the default accounts. If there are multiple BizTalk Server groups in an Active Directory forest, change the account names to avoid conflicts. BizTalk Server supports only `<NetBIOS domain name>\<user>` name formats for service accounts and Windows groups.

- **Account names with BAM Management Web Service**: BizTalk Server does not support built-in accounts or accounts without passwords for the BAM Management Web Service User.

  Configuring BizTalk Server with such accounts may appear to succeed, but the BAM Management Web Service fails.

  Use of such accounts for the BAM Application pool is supported.

- **Install and Uninstall**: When you uninstall BizTalk Server, manually delete the BizTalk Server databases. If you are installing BizTalk Server as a developer or evaluator, consider installing on a virtual machine. This way, if you have to reinstall, you can easily roll back to a preset checkpoint without having to go through the uninstall process.

- **32-bit and 64-bit computers**: There are few differences when installing BizTalk Server on 32-bit Windows or 64-bit Windows. This document covers both 32-bit and 64-bit installations. Differences between them are noted.

- **Workgroups**: Installing and configuring BizTalk Server in a workgroup environment on a single computer is supported. In this scenario, both SQL Server and BizTalk Server features and components are installed and configured on the same computer.

- **Terminal Server**: Installing BizTalk Server using Terminal Server running in application mode is not supported.

- **Silent Upgrade** is not supported.

- **Unsupported Applications**: BizTalk Server does not support custom applications built on unsupported APIs such as PAM APIs, stored procedures, or direct database access. Run at least one test upgrade before you upgrade your production environment.

- **SQL Server instances**: It’s a good practice to upgrade any SQL Server instances before you upgrade the platform.

## Prepare your computer for upgrade

1. Install critical Windows Updates. When the installation completes, it's recommended to restart your computer.
2. Install Microsoft OLEDB Driver for SQL Server on all BizTalk Server computers.
3. Install the x86 and x64 versions of Visual C++ 2015-2019 redistributable packages on all BizTalk Server computers.
4. Upgrade SQL Server to a supported version. For the supported versions, see [Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md). For more information on upgrading SQL Server, see [Upgrade SQL Server](/sql/database-engine/install-windows/upgrade-sql-server).
5. Upgrade SQL Server Client Tools. In a multicomputer environment, the Administration tools may be installed on a separate computer. Upgrade the SQL Server Administration Client Tools, including the Management Tools.
6. Install SQL Server Integration Services. In a multicomputer environment, the BAM Tools may be installed and configured on a separate computer. Install version of SQL Server Integration Services compatible with your target SQL Server.
7. Create the SSIS Catalog (SSISDB) on SQL Server.
8. Install Visual Studio. [Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md) lists the supported versions. Different Visual Studio versions can be installed side-by-side. For more information, see [Visual Studio](/visualstudio/install/install-visual-studio-versions-side-by-side).
9. Install Office. [Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md) lists the supported Office versions. See [Install and use different versions of Office](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF) on the same computer.
10. Stop the BizTalk Server services and Windows services:

    - BizTalk Service BizTalk Group: *<Application_Name>*
    - Rule Engine Update Service
    - World Wide Web Publishing Service

    If you have any BizTalk Server accelerators installed, stop the HL7 Logging Service.

11. Back up the databases:

    - Master
    - MSDB
    - BAMArchive
    - BAMPrimaryImport
    - BAMStarSchema
    - BizTalkDTADb
    - BizTalkMgmtDb
    - BizTalkMsgBoxDb
    - BizTalkRuleEngineDb
    - BAMAnalysis

    [SQL Server: Backup Overview](/sql/relational-databases/backup-restore/backup-overview-sql-server)

## Do the upgrade

> [!IMPORTANT]
> When you installed SQL Server, setup granted your logged-on account system administrator rights. System administrator rights are also required to install BizTalk Server. Do one of the following:
>
> - Use the same account you used when you installed SQL Server.
> **OR**
> - Make sure the current logged-on account has system administrator rights.

### Upgrade steps

1. Close all open programs.
2. Run **Setup.exe** from the installation media.
3. In Start, select **Install Microsoft BizTalk Server**.
4. In **Customer Information**, enter your user name, organization, and product key. Select **Next**.
5. Accept the license agreement, and select **Next**.
6. In Customer Experience Improvement Program, enter your preference. See [Appendix A](#appendix-a-customer-experience-improvement-program) (in this article) for more information.
7. In **Component Installation**, review the available components, and select **Next**.
8. In **Summary**, review the upgradable components.
9. Select **Upgrade** to start.
10. Optional: Select **Use the Microsoft Update when I check for updates (recommended)**.
11. In **Upgrade Completed**, clear the L**aunch BizTalk Server Configuration** check box, and then select **Finish**.

**ADDITIONAL**

A lot happens during an upgrade of BizTalk Server, and it’s not uncommon to run into an error during the process. However, most errors are easily remedied if you’re prepared. We recommend reading the [Appendix B](#appendix-b-known-issues) (in this article) for tips on how to avoid upgrade errors, and what to do if one occurs.

The upgrade process only upgrades features that were part of your previous version of BizTalk Server. New features are not installed during an upgrade. To install these features, rerun Setup after the upgrade, choose **Modify**, and select the features you want to install. Once installed, configure them using the **BizTalk Server Configuration Manager**.

To verify if the upgrade is successful, open **Programs and Features** and look for BizTalk Server 2020. If it’s listed, setup succeeded.

## Post upgrade

You cannot roll back to BizTalk Server 2016.

- **Install BizTalk Server extension in Visual Studio**: To complete BizTalk Developer Tools installation, install BizTalk Server extension in Visual Studio.

- **Download and copy WinSCP**: If your are using SFTP adapter, download recommended version of WinSCP zip file and extract it to BizTalk Server 2020 installation folder.

- **Uninstall OWC**: OWC is deprecated and not supported by Microsoft. It is recommended that you uninstalled it from BizTalk Server machines. Impact is limited to Aggregation Viewer capability in BAM Portal.

- **Install MQSAgent**: If the MQSAgent.dll file is installed on a remote WebSphere MQ Server, install a new version of the MQ Agent from BizTalk Server 2020 on the remote WebSphere MQ Server.

- **Start MSMQ**: If you use the MSMQ adapter, start the Message Queuing service.

- **SQL Agent job**: Reconfigure the following SQL Server Agent jobs:

  - DTA Purge and Archive (BizTalkDTADb): See [How to Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md)
  - Backup BizTalk Server (BizTalkMgmtDb): See [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)

- **Scheduled BAM DTS packages**: If you have SQL Agent jobs to schedule BAM DTS packages, reconfigure the jobs to use SSIS packages from SSIS Catalog (SSISDB) instead of SSIS Package Store (MSDB).

- **Enable Auditing**: If you want to enable auditing for BizTalk management operations, Enable Auditing through BizTalk Group Settings.

- **BizTalk Server Read Only Users group**: If you want to configure Read Only Users role, run PowerShell script Configure-WindowsGroupForReadOnlyUserDBRole.ps1 with windows group as parameter. Make sure that you have SQL Server powershell module installed.

- **BizTalk Server 2016 Feature Pack**: If you upgraded from BizTalk Server 2016 Feature Pack, below post upgrade actions are required.

  - **O365 Adapters**: Install and configure BizTalk TMS if you use O365 adapters. You will need to **activate** each port using these adapters by logging into your outlook account once for every port. 

  - **Management Service and Operational Data Service**: If you use Management Service or Operational Data Service, delete exising Management Service and Operational Data Service in IIS Manager, delete corresponding App Pools, and then re-configure BizTalk REST API feature in BizTalk Server 2020 configuration.

- **Restart applications**: Restart all deployed applications that are upgraded.

- **Update Host to 64bit for TIBCO Enterprise Message Service Adapter**: Update the Send and Receive Handler host for TIBCO Enterprise Message Service Adapter to a 64 bit host.

## Appendix A: Customer experience improvement program

As part of the Customer Experience Improvement Program in BizTalk Server, you can provide useful feedback to Microsoft regarding feature usage of BizTalk Server. The data collected is anonymous, and cannot be used to identify you. Microsoft collects feature usage statistics as part of this program.

By participating in this program, you can help improve the reliability and performance of various features of BizTalk Server. 

## Appendix B: Known issues

- **Configure BAM Alerts on Administration computer**: There is a multicomputer environment with the Administration, Runtime, and SQL Server components installed on separate computers. When working with BAM Tools or BAM Alerts, the following issues can occur:

  **ISSUE**: When you configure BAM Tools on a BizTalk Administration computer, the following error occurs:

  `Service BAMAlerts was not found on computer ‘.’.The specified service does not exist as an installed service.`

  **ISSUE**: When you deploy a BAM Activity Definition from Runtime computer, the following error occurs:

  `A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)`

  This occurs if BAM Alerts is configured on the Runtime computer. To resolve, configure BAM Alerts on the same computer as the BizTalk Administration console. Do not configure BAM Alerts on the Runtime computer.

- **Recovering from a Failed Upgrade**: A failed upgrade can occur at any time during the upgrade. How you recover from a failed upgrade is determined from what point during each phase the failure occurred.

  - If the upgrade fails when installing the prerequisites, then setup stops further installation of prerequisites, and returns a message with the error. You can then correct the problem and rerun setup.

  - If the upgrade fails when upgrading the databases, removing features from the existing BizTalk Server version, or installing the new version, then setup stops further installation, and returns a message with the error. Any changes are rolled back. Changes made to the BizTalk Server databases cannot be rolled back.

    If components of the previous BizTalk Server installation are removed during upgrade, your computer may be left in a state with no BizTalk Server components. Feature configuration information from the previous installation may be retained. And depending on where the upgrade process fails, the BizTalk Server databases may have been upgraded. It may be necessary to restore the databases which you backed up earlier before running setup again.

  - If the upgrade fails when reconfiguring the BizTalk Server features, then the setup returns a message with the level of completion. If configuration upgrade fails or partially succeeds, run the BizTalk Server configuration to complete the upgrade.

    If the upgrade continues to fail and you need to regress to your previous version of BizTalk Server, you must restore the databases you backed up, and then reinstall your previous BizTalk Server version.

- **Use the same versions**: In a BizTalk application group, you cannot run machines with different versions of BizTalk Server. For example, in the BizTalk Administration Console, you cannot bind a send port running on one version of BizTalk Server to a receive location running on a different version of BizTalk Server.

- **Certificate Store**: After you upgrade, you open a send port or receive location from the BizTalk Server Administration console, and get error: `Could not open certificate store, the system cannot find the file specified (System).`

  This error occurs if the certificate store is missing.

- **BAM Portal**: On a 64-bit machine, you cannot access BAM portal after you upgrade. Possible resolution:

  1. Create a backup copy of the web.config file located at `%BizTalkInstallDir%\BAMPortal\web.config`.

  2. Using bm.exe in the BizTalk Server Tracking folder, run the following at the command prompt: `bm.exe get-config –FileName:<filepath> -Server:MyServer -Database:MyDB`

      From the Config XML file, get the value for *BAMVRoot* (xpath: BAMConfiguration\ GlobalProperty\Name="BAMVRoot").

  3. Open the BizTalk Server Configuration on the computer that is listed as the BAMVRoot value, and unconfigure the BAM portal.

  4. Open the BizTalk Server Configuration, and configure the BAM portal.

  5. Open the new web.config file from location mentioned in step (1).

  6. Using the backup copy of the web.config file, set the following values (under `configuration\appSettings`):

      - key="MainPageContentUrl"
      - key="AlertNotificationOptions"

     > [!NOTE]
     > On a 64-bit machine, after you upgrade the operating system, we recommend that you reconfigure the BAM portal.

- **Deploy EDI BAM activities**: When you upgrade, the upgrade may partially succeed. This can happen when you upgrade SQL Server (with EDI configured). The EDI BAM activities might not be upgraded properly. To resolve this issue, deploy the BAM activities by running the following commands at the command prompt with administrative credentials:

  `"<BizTalk Installation Folder>\Tracking\bm.exe" deploy-all -DefinitionFile:"<BizTalk Installation Folder>\AS2ResendActivityDefs.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

  `"<BizTalk Installation Folder>\Tracking\bm.exe" update-all -DefinitionFile:"<BizTalk Installation Folder>\Microsoft.BizTalk.Configuration.EdiAS2.UpgradeR2toR3.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

  `"<BizTalk Installation Folder>\Tracking\bm.exe" update-all -DefinitionFile:"<BizTalk Installation Folder>\Microsoft.BizTalk.Configuration.Batching.UpgradeR2toR3.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

- **SSO Error on Cluster**: On a BizTalk Server runtime cluster environment, when you try to upgrade, you may receive an error message:

  `SSO Master Secret Server service is not running on <Cluster name>.Please start the service to continue the upgrade.`

  To resolve this issue, refresh the SSO services both in the SSO and BizTalk Server runtime cluster.

  **To refresh the SSO services in SSO cluster**:

  1. In Cluster Administrator, **Bring Online** the cluster group that contains the clustered Enterprise SSO service resource. This should start all of the resources in the cluster group.

  2. **Take Offline** the clustered instance of the Enterprise SSO service. And then, bring it back **Online**.

  3. **Move** the cluster group. This step should move the cluster group that contains the clustered Enterprise SSO services resource from the first node to the second node.

  4. **Take Offline** the clustered instance of the Enterprise SSO service. And then, bring it back **Online**.

     **To refresh the SSO services in a BizTalk Server Runtime cluster**:

  5. In Cluster Administrator, **Bring Online** the cluster group that contains the clustered BizTalk Server runtime resource. This should start all of the resources in the cluster group.

  6. **Take Offline** the clustered instance of the Enterprise SSO services. And then, bring it back **Online**.

  7. **Move** the cluster group. This step should move the cluster group that contains the clustered BizTalk Server runtime resource from the first node to the second node.

  8. **Take Offline** the clustered instance of the Enterprise SSO services. And then, bring it back **Online**.

## Next steps

[Post-configuration steps to optimize your environment](post-configuration-steps-to-optimize-your-environment.md)
