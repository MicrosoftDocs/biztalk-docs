---
title: "Upgrade to BizTalk Server 2016 | Microsoft Docs"
ms.custom: ""
ms.prod: biztalk-server
ms.date: "06/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 975ec82b-ed27-4545-8e4a-0e567507c9ba
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Upgrade to BizTalk Server 2016
Upgrading to [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] from [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)], or BizTalk Server 2013.

This topic provides an overview of the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] upgrade process, key information, and step-by-step instructions for upgrading from BizTalk Server 2013 R2 or BizTalk Server 2013.


## Upgrade overview

- Read this entire document before you upgrade. BizTalk Server connects many disparate components, both internal and external, to your enterprise. Most real-world deployment scenarios extend much farther to include multiple servers and eventually clusters of both physical and virtual computers.

- No two BizTalk Server deployments are the same. Before you upgrade, gather information on your enterprise needs, and discuss the scope of your deployment with the IT Professionals, System Administrators, and Developers who use BizTalk Server. By studying this upgrade guide, and determining the specific needs of your enterprise, you are creating your own deployment roadmap.

- Use the BizTalk Server Best Practices Analyzer (BPA) to examine a BizTalk Server deployment, and generate a list of best practices. BPA performs configuration-level verification, by reading and reporting only, and uses the gathered data to determine whether best practices are being followed.

### Planning your upgrade

The following is a high-level view of the upgrade process. Each of the steps listed must be run in the order shown.

- Operating systems upgrade paths
- Microsoft SQL Server® upgrade paths
- Windows® SharePoint® Services upgrade
- Install Visual Studio side-by-side
- Install Microsoft Office 2016/2013 side-by-side

### Supported upgrade paths
The following table lists the supported operating systems that can be upgraded to [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. “Yes” means the BizTalk Server version running on that operating system can be upgraded. “No” means the BizTalk Server version running on that operating system cannot be upgraded. When “No”, the BizTalk environment must be recreated on a supported operating system.  [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) lists the supported operating systems.

| Operating Systems | BizTalk Server 2013 R2 |BizTalk Server 2013 |
| --- | --- | --- |
| Windows Server 2012 R2 | Yes | No |
| Windows Server 2012 | No | No |
| Windows 8.1 | Yes | No |
| Windows 8 | No | No
| Windows 7 SP1 | No | No |

The following table lists the supported SQL Server versions that can be upgraded to [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. The SQL Server hosts the databases used by BizTalk Server. “Yes” means BizTalk Server using that SQL Server version can be upgraded. “No” means BizTalk Server using that SQL Server version cannot be upgraded. When “No”, the BizTalk environment must be recreated on a supported SQL Server version. [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) lists the supported SQL Server versions. 

> [!TIP]
> If you're SQL Server version isn't supported, or isn't in the following list, then review the SQL Server upgrade documentation. The SQL upgrade covers more versions than what BizTalk supports. For example, if you're using SQL Server 2008, you may be able to upgrade SQL Server 2016. Then, you can upgrade to [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. [Upgrade to SQL Server 2016](https://msdn.microsoft.com/library/bb677622.aspx) and [Upgrade to SQL Server 2014](https://msdn.microsoft.com/library/bb677622(v=sql.120).aspx) lists the SQL Server versions that can be upgraded.

| SQL Server | BizTalk Server 2013 R2 |BizTalk Server 2013 |
| --- | --- | --- |
| SQL Server 2014 | Yes | No |
| SQL Server 2012 SP1| No | No |
| SQL Server 2012 | No | No |
| SQL Server 2008 R2 SP1 | No | No |


The following table lists the supported Edition upgrade path from [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 to [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. “Yes” means the [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 edition can be upgraded to the edition. “No” means the [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 edition cannot be upgraded to the edition. When “No”, the BizTalk environment must be recreated.

| BizTalk Server 2013 R2/2013 | BizTalk Server 2016 Evaluation Edition | BizTalk Server 2016 Branch Edition | BizTalk Server 2016 Developer Edition | BizTalk Server 2016 Standard Edition | BizTalk Server 2016 Enterprise Edition |
| --- | --- | --- | --- | --- | --- |
| Evaluation | No | No | No | No | Yes | 
| Branch | No | Yes | No | No | Yes | 
| Developer | No | No | Yes | No | Yes | 
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

    [Windows 7 and Windows Server 2008 R2: Import a Certificate](http://technet.microsoft.com/library/cc754489.aspx)  
    [Windows 7 and Windows Server 2008 R2: Export a Certificate](http://technet.microsoft.com/library/cc730988.aspx)  

- **DTC**: Enable Microsoft Distributed Transaction Coordinator (MSDTC) ([Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)), and then enable the Inbound/Outbound DTC rules:

    1. In Server Manager, select **Tools**, and open **Windows Firewall with Advanced Security**.
    2. Select **Inbound Rules**.
    3. In **Inbound Rules**, right-click **Distributed Transaction Coordinator** * (as appropriate), and then **Enable Rule**.
    4.  In Windows Firewall with Advanced Security, select **Outbound Rules**.
    5.  In **Outbound Rules**, right-click **Distributed Transaction Coordinator** * (as appropriate), and then **Enable Rule**.

- **SharePoint**: The Client Side Object Model (CSOM) is used to connect to SharePoint Services. The  Server Side Object Model (SSOM) (the web service) is removed in [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].

    If you are using SharePoint versions that doesn't support CSOM, you may be able to upgrade to a supported SharePoint version:

    [Upgrade to SharePoint 2016](https://technet.microsoft.com/library/cc303420(v=office.16).aspx)  
    [Upgrade to SharePoint 2013](https://technet.microsoft.com/library/cc303420(v=office.15).aspx)

- **.NET Framework**: There is no concept of side-by-side installation between .NET Framework 4.5 and .NET Framework 4.6. The .NET Framework 4.6 binaries overwrite .NET Framework 4.5 binaries. .NET Framework 4.6 is a [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] requirement, and is not supported (and should not be installed) in previous BizTalk Server versions.

- **Office 2016 and Office 2013**: [Install and use different versions of Office](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF) on the same computer. Also, check out [these issues](https://support.microsoft.com/kb/3094527).

- **BizTalkServerApplication Host**: The upgrade requires the existence of the default host. If the default host instance associated with the SQL Adapter send ports and receive locations is removed, associate the default host to the SQL Adapter before upgrading. After upgrade is complete, you can remove the default host from the list.

- **Custom Bindings**: User-defined custom bindings that are built with earlier versions of the .NET Framework are not available after you upgrade. To use the custom bindings, manually add the custom bindings in the .NET Framework 4.6 machine.config file.

- **Configuration Files**: Back up all custom configuration files in BizTalk Server 2013 R2/2013. BizTalk Server supports migration of changes only in the `btsntsvc.exe.config` and `bm.exe.config` files.



### BAM Alerts

SQL Server Database Mail is required to use BAM Alerts. If SQL Server is being upgraded from a SQL version that used existing BAM Alert definitions with Notification Services, then you can back up your BAM alert definitions, and deploy them after upgrading. Use the BM.exe command line tool (`\Program Files (x86)\Microsoft BizTalk Server <your version>\Tracking`). Specific steps include:

1. Open a command prompt and go to `\Program Files (x86)\Microsoft BizTalk Server <your version>\Tracking`.
2. Create a definition file in the command prompt: `bm.exe get-defxml -FileName:YourBAMDefinition.xml`
3. In [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 Configuration, unconfigure BAM Alerts.
4. Upgrade to SQL Server 2016 or SQL Server 2014 SP1.
5. Configure SQL Server Database Mail.
6. Upgrade to [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].
7. In [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Configuration, configure BAM Alerts.
8. Deploy the saved definition file in the command prompt: `bm.exe update-all -DefinitionFile:YourBAMDefinition.xml`

> [!IMPORTANT]
> If you don’t follow these steps in the order listed or create a definition file, you must recreate the definition files after the BizTalk Server upgrade.
> 
> To view the BM.exe help, type: `bm.exe help`.


### BAM 

- **BAM DTS Packages**: Stop all BAM Data Transformation Services (DTS) packages. Otherwise, data may be lost or an online analytical processing (OLAP) cube may corrupt. 

- **Disk Space**: The free disk space should be at least the size of the existing BAM databases.

- **Real-time Aggregations**: If you are using BAM real-time aggregations in your current version of BizTalk Server and are upgrading SQL Server, install or upgrade to the SQL Server Enterprise Edition. Otherwise, the upgrade fails.

- **maxTimeout value**: If you have a large BAM database, update the `maxTimeout` value for distributed transactions in your machine.config file to:  

    ```
    <system.transactions>
       <machineSettings maxTimeout="23:59:59" />
    </system.transactions>
    ```

- **BAM tracking enabled with Tracking Profile Editor (TPE)**: After you upgrade, tracking profiles that were previously deployed are upgraded; however, their corresponding interceptor configurations are not upgraded. Any new intercepted BAM messages may still have the BizTalk Server 2013 R2/2013 references. To upgrade the corresponding interceptor configurations, use the Tracking Profile Editor to retrieve the profile for the activity, and then reapply the profile.

- **LiveData Workbook**: If you are using BAM in BizTalk Server 2013 R2/2013, after the upgrade, you must manually regenerate the LiveData Workbook. To regenerate the LiveData Workbook:

  1. Retrieve the BAM Definition by running the following command:  
     `BM get-defxml MyDef.xml`
  2. Re-create the PivotTable reports by opening Microsoft Office Excel, and then selecting the BAM Add-ins. Import the *MyDef.xml* file created in step (1), and recreate the PivotTable reports. Save the new BAM Workbook as *MyNewBook.xls*.
  3. Rename the PivotTable reports by finding the PivotTable names in *MyDef.xml* under `<Caption>` in the  `<BAMDefinition>\<Extension>\<OWC>\<PivotTableView>\<PivotTable>\<PivotView>\<Label>` path. Use these names to rename your PivotTable reports in *MyNewBook.xls*.
  4. Regenerate the LiveData Workbook by running the following command:  
     `BM regenerate-livedataworkbook MyNewBook.xls`

     > [!NOTE]
     > Regenerated LiveData Workbooks do not recreate the Excel artifacts (for example, charts) in the original LiveData Workbook. Manually recreate the artifacts.


### Enterprise Single Sign-On (ESSO)

|                            Scenario                            |                                                                                                                                                                                                                                                                                                                                          More info                                                                                                                                                                                                                                                                                                                                          |
|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Upgrading from an earlier version of Enterprise Single Sign-on | BizTalk Server includes an updated version of Enterprise Single Sign-On (ESSO). If you are installing this release on a computer with an earlier version of BizTalk, ESSO is automatically updated during setup. We recommend that you perform the following steps before upgrading: <br/><br/> 1. Verify that a current version of the Single Sign-On database (SSODB) is backed up to a secure location. <br/>2. Verify that the current master secret key is backed up to a secure location.<br/>3. Know the password to the master secret.<br/><br/>Upgrade all the servers in a BizTalk group to the same release. This requirement also applies to a standalone master secret server. |
|  Upgrade using the Enterprise Single Sign-On standalone setup  |             Use the following steps to perform an upgrade on computers that have a standalone Enterprise Single Sign on installation, such as a dedicated master secret server.<br/><br/>1. Verify that the current master secret key is backed up to a secure location.<br/>2. Verify that a current version of the SSODB is backed up to a secure location.<br/>3. Run the ESSO **Setup.exe** from the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] installation media. The default installation folder is `\Platform\SSO`.<br/>4. In the **Autorun** dialog box, select **Microsoft Enterprise Single Sign-On**.<br/>5. In the Summary dialog box, select **Upgrade**.              |

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

- **BizTalk Assembly Viewer** is not supported on a 64-bit operating system.

- **Install and Uninstall**: When you uninstall BizTalk Server, manually delete the BizTalk Server databases. If you are installing BizTalk Server as a developer or evaluator, consider installing on a virtual machine. This way, if you have to reinstall, you can easily roll back to a preset checkpoint without having to go through the uninstall process.

- **32-bit and 64-bit computers**: There are few differences when installing BizTalk Server on 32-bit Windows or 64-bit Windows. This document covers both 32-bit and 64-bit installations. Differences between them are noted.

- **Workgroups**: Installing and configuring BizTalk Server in a workgroup environment on a single computer is supported. In this scenario, both SQL Server and BizTalk Server features and components are installed and configured on the same computer.

- **Terminal Server**: Installing BizTalk Server using Terminal Server running in application mode is not supported. See [KB 832027](https://support.microsoft.com/kb/832027).

- **Silent Upgrade** is not supported.

- **Unsupported Applications**: BizTalk Server does not support custom applications built on unsupported APIs such as PAM APIs, stored procedures, or direct database access. Run at least one test upgrade before you upgrade your production environment.

- **SQL Server instances**: It’s a good practice to upgrade any SQL Server instances before you upgrade the platform.

## Prepare your computer for upgrade

|                 Task                  |                                                                                                                                                                                                                                        Info                                                                                                                                                                                                                                         |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Install Critical Windows Updates    |                                                                                                                                                                                                Select Windows Update from the Programs menu. You may need to restart your computer.                                                                                                                                                                                                 |
|      Save BAM Alert Definitions       |                                    Applies only if you currently use existing BAM Alert definitions with SQL Server Notification Services. Create a definition file using BM.exe and unconfigure BAM Alerts in the [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 Configuration.<br/><br/>**Before the upgrade** (in this topic) lists the specific steps.<br/><br/>Otherwise, recreate the BAM Alert definitions after you upgrade.                                    |
|          Upgrade SQL Server           |                                         Upgrade to a supported SQL Server version. See:<br/><br/>[Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)<br/>[Upgrade to SQL Server 2016](https://msdn.microsoft.com/library/bb677622.aspx)<br/>[Upgrade to SQL Server 2014](https://msdn.microsoft.com/library/bb677622(v=sql.120).aspx)                                          |
|    Upgrade SQL Server Client Tools    |                                                                                                                                                In a multicomputer environment, the Administration tools may be installed on a separate computer. Upgrade the SQL Server Administration Client Tools, including the Management Tools.                                                                                                                                                |
|         Install Visual Studio         |                         See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) for the supported versions. Different Visual Studio versions can be installed side-by-side. See [Visual Studio 2015](https://msdn.microsoft.com/library/ms246609(v=vs.140).aspx) and [Visual Studio 2013](https://msdn.microsoft.com/library/ms246609(v=vs.120).aspx).                         |
|            Install Office             |                                     See [Install and use different versions of Office](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF) on the same computer. [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) lists the supported Office versions.                                     |
| Stop the BizTalk and Windows Services |                                                                                                      - BizTalk Service BizTalk Group:  *<Application_Name>*<br/>- BizTalk Base EDI Service<br/>- Rule Engine Update Service<br/>- World Wide Web Publishing Service<br/><br/>**NOTE**<br/>If you have any BizTalk Server accelerators installed, stop the HL7 Logging Service.                                                                                                      |
|         Back up the databases         | - Master<br/>- MSDB<br/>- BAMArchive<br/>- BAMPrimaryImport<br/>- BAMStarSchema<br/>- BizTalkDTADb<br/>- BizTalkEDIDb<br/>- BizTalkHwsDb<br/>- BizTalkMgmtDb<br/>- BizTalkMsgBoxDb<br/>- BizTalkRuleEngineDb<br/>- TPM<br/>- BizTalkAnalysisDb<br/>- BAMAnalysis<br/><br/>[SQL Server 2014: Backup Overview](https://technet.microsoft.com/library/ms175477(v=sql.120).aspx)<br/>[SQL Server 2012: Backup Overview](https://technet.microsoft.com/library/ms175477(v=sql.110).aspx) |
|  Configure SQL Server Database Mail   |                                                                                                                      Applies only if you use BAM Alert definitions with SQL Server Notification Services.<br/><br/>**Before the upgrade** (in this topic) lists the specific steps.<br/><br/>Otherwise, recreate the BAM Alert definitions after you upgrade.                                                                                                                       |

## Do the upgrade

> [!IMPORTANT]
> When you installed SQL Server, setup granted your logged-on account system administrator rights. System administrator rights are also required to install BizTalk Server. Do one of the following:
> 
> - Use the same account you used when you installed SQL Server  
> **OR**  
> - Make sure the current logged-on account has system administrator rights

### Upgrade steps

1. Close any open programs.
2. Run **Setup.exe** from the installation media.
3. In Start, select **Install Microsoft BizTalk Server**.
4. In **Customer Information**, enter your user name, organization, and product key. Select **Next**.
5. Accept the license agreement, and select **Next**.
6. In Customer Experience Improvement Program, enter you preference. See **Appendix A** (in this topic) for more information.
7. In **Component Installation**, review the available components, and select **Next**.
8. If your computer is missing a prerequisite, Setup can install the redistributable prerequisites. You can either:

    - Select Automatically install the redistributable prerequisites from the web  

      OR  

    - Select Automatically install the redistributable prerequisites from a CAB file if you downloaded the CAB file. Browse to the location of the CAB file and select it.

9. In **Summary**, review the upgradable components.
10. Select **Upgrade** to start.
11. Optional: Select **Use the Microsoft Update when I check for updates (recommended)**.
12. In **Upgrade Completed**, clear the L**aunch BizTalk Server Configuration** check box, and then select **Finish**.

**ADDITIONAL**  
A lot happens during an upgrade of BizTalk Server, and it’s not uncommon to run into an error during the process. However, most errors are easily remedied if you’re prepared. We recommend reading the **Appendix B** (in this topic) for tips on how to avoid upgrade errors, and what to do if one occurs.

The upgrade process only upgrades features that were part of your previous version of BizTalk Server. New features are not installed during an upgrade. To install these features, rerun Setup after the upgrade, choose **Modify**, and select the features you want to install. Once installed, configure them using the **BizTalk Server Configuration Manager**.

To verify if the upgrade is successful, open **Programs and Features** and look for [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. If it’s listed, setup succeeded.

## Post upgrade
You cannot roll back to [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013.

- **If you created a BAM Alerts definition XML file**: In [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Configuration, configure BAM Alerts. Then, deploy the saved Definitions.

    **Before the upgrade** (in this topic) lists the specific steps. Otherwise, recreate the BAM Alert definitions after you upgrade.

- **Install MQSAgent**: If the MQSAgent.dll file is installed on a remote WebSphere MQ Server, install a new version of the MQ Agent from [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] on the remote WebSphere MQ Server.

- **Start MSMQ**: If you use the MSMQ adapter, start the Message Queuing service.

- **Custom EXE and BRE**: If you have a custom managed executable file that references Business Rule Engine assembly in BizTalk Server 2010, add the following to the application configuration file to run the process in the .NET Framework 2.0.

    ```
    <?xml version="1.0" encoding="Windows-1252"?>
    <configuration> 
     <startup>
      <supportedRuntime version="v2.0.50727" />
     </startup>   
    </configuration>
    ```

- **SQL Agent job**: Reconfigure the following SQL Server Agent jobs:

    -   DTA Purge and Archive (BizTalkDTADb): See [How to Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md)
    -   Backup BizTalk Server (BizTalkMgmtDb): See [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)

- **Restart applications**: Restart all deployed applications that are upgraded.

- **BAM Portal error**: When you open the BAM portal, you may receive the following error message: 

    `The server encountered a critical failure while trying to access the list of Views. The Business Management Web Service requires Administrator's attention.` 

    This error can occur if the BAM portal is configured on a website used by applications that are running .NET Framework 2.0. In this scenario, host the BAM portal on a new website. To add a website, see [Create a Web Site](http://go.microsoft.com/fwlink/p/?LinkID=196470). After creating the website, reconfigure the BAM Portal:

    1. Open **BizTalk Server Configuration**.
    2. Select **Unconfigure Features**. In **Unconfigure Features**, select the **BAM Portal** check box, and select **OK**.
    3. Reconfigure the BAM portal by selecting the new website from the **BAM Portal Web Site** list.

- **BizTalk 2016 Accelerator for SWIFT**: The BizTalk Server upgrade process does not update an edited *BREDeployment.exe.config* file. Manually change the paths in the *BREDeployment.exe.config* file located in the `\Program Files\Microsoft BizTalk 2016 Accelerator for SWIFT\SDK\Tools` folder.

    Also, the A4SWIFT Web Services and Message Pack configuration is lost. Reconfigure these after BizTalk Server is upgraded.

## Appendix A: Customer experience improvement Program
As part of the Customer Experience Improvement Program in BizTalk Server, you can provide useful feedback to Microsoft regarding feature usage of BizTalk Server. The data collected is anonymous, and cannot be used to identify you. Microsoft collects feature usage statistics as part of this program.

By participating in this program, you can help improve the reliability and performance of various features of BizTalk Server. For more information about this program and its privacy policy, see [Microsoft BizTalk Server CEIP Privacy Policy](http://go.microsoft.com/fwlink/p/?LinkId=188553).

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

- **Restart SSO Service**: If you have a previous Visual Studio version or .NET Framework 4.5 installed on your machine, then the SSO service in earlier versions of BizTalk Server stops working. To resolve this issue, run the `regasm SSOSQL.dll` command from the Visual Studio command prompt. This command restarts the SSO service.

    > [!NOTE]
    > On a 64-bit computer, run the 32-bit and 64-bit versions of the regasm command.

- **Unable to use SOAP**: After a platform upgrade, you may not be able to send SOAP message because of permissions. To resolve this, edit the Web.config file at `C:\inetpub\wwwroot\<SOAPExternalAppName>\` with the following text:

    ```
    <securityPolicy>
    <trustLevel name="Full" policyFile="internal" />
    <trustLevel name="High" policyFile="web_hightrust.config" />
    <trustLevel name="Medium" policyFile="web_mediumtrust.config" />
    <trustLevel name="Low" policyFile="web_lowtrust.config" />
    <trustLevel name="Minimal" policyFile="web_minimaltrust.config"/>
    </securityPolicy>
    <trust level="Full" originUrl="" processRequestInApplicationTrust="true"/>
    ```

    You may also have to change the custom error mode from **Remote Only** to **Off**.

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
