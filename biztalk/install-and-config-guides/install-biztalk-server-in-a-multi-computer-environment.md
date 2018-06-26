---
title: "Install BizTalk Server in a Multi-Computer Environment | Microsoft Docs"
description: Multi-server installation and setup guidance when BizTalk and SQL Server are installed on a different computers, including BAM
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4d0e707-6b9e-49e1-9f17-19b3bac1229e
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install BizTalk Server in a Multi-Computer Environment

## Overview

There are many things to consider when planning a multicomputer installation of Microsoft® BizTalk® Server. Often the network infrastructure exists and BizTalk Server must coexist with other network applications. This guide describes some of the considerations that apply to the BizTalk Server and Business Activity Monitoring (BAM) installation in a multicomputer, distributed deployment. This information helps you plan the installation and configuration of BizTalk Server and Business Activity Monitoring (BAM) and the applications and components it depends on.

The single server installation guide contains important procedures and more background information that is not duplicated in this document. For example, the following information is discussed in detail in the single server installation guide:

- Detailed installation procedures
- Descriptions of BizTalk Server features and dependencies
- Details of BizTalk Server basic configuration settings
- Software and hardware requirements
- CAB file redistributable component list

## High availability
BizTalk Server provides a high availability solution that uses network load balancing (NLB) clustering and failover clustering, and SQL Server Always On using Availability Groups (AG). A high availability solution helps minimize the downtime if there is a hardware or software failure. 

**NLB and failover clusters** complement each other in complex architectures. NLB clustering is used for to load balance requests between front-end web servers. Failover clustering provides high availability for the BizTalk Server in-process hosts, the Enterprise Single Sign-On Master Secret Server and BizTalk Server databases. This is typically used for on-premises environments. The following are good resources: 

* [BizTalk Server: High Availability Survival Guide](http://social.technet.microsoft.com/wiki/contents/articles/6532.biztalk-server-high-availability-survival-guide.aspx)

* [Improving Fault Tolerance in BizTalk Server by Using a Windows Server failover cluster or Windows Server cluster](http://go.microsoft.com/fwlink/p/?LinkId=154499)

**SQL Server Always On AG** can be used with on-premises environments, and with Azure virtual machines. AG support starts with BizTalk Server 2016, and is supported in any newer versions of BizTalk Server. AG includes primary database replicas, and secondary database replicas. BizTalk Server connects to the primary database replicas, while the secondary database replicas provide redundancy and fail over. [Always On Availability Groups (SQL Server)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server) provides details on AG works. 

[BizTalk HA using SQL Server Always On AG](../core/high-availability-using-sql-server-always-on-availability-groups.md) provides more details from a BizTalk-perspective.

## Separate runtime and administration
BizTalk Server supports various installation scenarios in the production environment. For example, you can install, configure, and deploy a runtime-only installation on one computer and an administration tools-only installation on a second computer.

During an Administration tools-only installation, the following components are installed: BizTalk Administration console, BM.exe, and BTSDeploy.exe. Consider the following when creating an Administration Tools-only BizTalk Server installation:

- SQL Server Agent must be running on all computers that are hosting BizTalk Server MessageBox databases. SQL Server Agent is required to track message bodies in the BizTalk Server Messaging engine.

- When you run the BizTalk Server Configuration Wizard, you create an Analysis Services database.

- Using the BizTalk Tracking database with SQL Server Analysis Services is not supported.

- Using named instances of SQL Server Analysis Services is not supported.

To install only Administration tools for BizTalk Server, select only **Administration Tools** during Setup. After the installation is complete, open the custom configuration manager and join an existing Enterprise Single Sign-On (SSO) system and BizTalk group.
Top of page

## Enable MSDTC
Before installing and configuring BizTalk Server in a multicomputer environment, enable network DTC access and network COM+ access on all BizTalk servers and any remote SQL Server instances used by BizTalk Server. See [Post-configuration steps to optimize your environment](post-configuration-steps-to-optimize-your-environment.md).

Additional:

- All BizTalk servers and SQL Servers in a group must have the same remote procedure call (RPC) authentication level applied. The DTC proxy may not correctly authenticate DTC when the computers use different operating systems, are joined to workgroups, or are in different domains that do not trust each other. See [MSDTC Fails to Mutually Authenticate](https://msdn.microsoft.com/library/ms686976(VS.85).aspx).

- If using a firewall, open the required DTC and RPC ports. See [Service overview and network port requirements for Windows](http://support.microsoft.com/kb/832017).

- To ensure that the DTC settings are correct, use the DTC Tester and DTC Ping tools. These tools and more DTC troubleshooting are described at [BizTalk Server - Troubleshooting Problems with MSDTC](https://social.technet.microsoft.com/wiki/contents/articles/2031.biztalk-server-troubleshooting-problems-with-msdtc.aspx).

## Remote SQL Server
When SQL Server is installed on a remote computer:

- [SQL Server Management Tools](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) (newer SQL versions) or SQL Server Client Tools Connectivity (older SQL versions) must be installed on the local BizTalk Server computer when SQL Server is remote. The SQL Server Tools installs the client libraries required to communicate with the remote instance of SQL Server. The version of the SQL Server tools on the local BizTalk Server computer must be the same version that is installed on the remote SQL Server.

- SQL Server OLAP client must be installed on the local computer if you plan to use Analysis Services remotely. The OLAP client may be included with [SQL Server 2016 Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).

- The remote SQL Server must be running during BizTalk Server configuration.

- The TCP and UDP ports you specified during the SQL Server setup process must be open during BizTalk Server configuration.

- To configure BAM tools, install SQL Server Management Tools - Basic and Complete on the BizTalk BAM Server. For more information about setting up and configuring BAM in a multi-computer environment, see [Install and Configure BAM (Business Activity Monitoring) in a Multi-Computer Environment](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx). 

- Named instances of SQL Server Analysis Services are not supported.

### SQL Server Topologies
SQL Server can be installed locally on the BizTalk Server, or on another server dedicated to SQL Server. Most production scenarios include BizTalk Server and SQL Server installed on separate computers. 

For a list of the supported SQL Server versions, see: 

* [BizTalk Server 2016 software requirements](hardware-and-software-requirements-for-biztalk-server-2016.md) 
* [BizTalk Server 2013R2 and 2013 software requirements](hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)

> [!IMPORTANT]
> Any additional service packs and Windows Updates are supported and should be installed.

### Maintain and troubleshoot databases

See [How to maintain and troubleshoot BizTalk Server databases](http://support.microsoft.com/kb/952555).

## Business Activity Monitoring (BAM)
BizTalk Server provides several tools for information workers, among them BAM. A basic understanding of the component architecture helps you plan the BizTalk Server installation to utilize the server resources available to you.
Business Activity Monitoring (BAM) is a collection of tools used to manage aggregations, alerts, and profiles to monitor relevant business metrics, known as key performance indicators or KPIs.

BAM is a module that gives you end-to-end visibility into your business processes to provides information about the status and results of various operational processes and transactions. You can use the BAM output to address problem areas and resolve issues within your business. For more information about BAM life cycle, see Business Activity Monitoring (BAM) poster at [BizTalk Server BAP posters](https://www.microsoft.com/download/details.aspx?id=56123).

BAM consists of the following layers:

| Layer | What it does | Examples | Where installed |
|---| ---|---|---|
| Presentation and Tools | Provides front-end services to business users and developers. Displays data, allows business users and developers define and manage templates and profiles; among other functions. | Office Excel, BAM Portal | Excel, management tools, and custom user interfaces are installed on the business user's or developer's workstation. The BAM portal and custom web applications built on the BAM infrastructure are installed on a server. |
| Web Services and Processing | Link the presentation and database layers; implementation of business rules and processes; data aggregation and analysis. | Windows SharePoint Services (WSS), Trading Partner Management Web Service, BAM Management Web Service, and the BizTalk Server engine. | On a server with IIS, SQL Notification service, and possibly custom web services, depending on the application. The BizTalk host services can also be installed on this server, or on a separate server in multiple computer configuration that has three or more computers. |
| Database and Platform Services | Data storage and retrieval; security and authentication; networking; operating system functions | SQL Server, Windows Server, Enterprise Single Sign-On (SSO), and fail-over and NLB clustering | On a server with Windows Server, SQL Server. For performance reasons, this server typically does not run the BizTalk host services. |

### Install BAM
Step-by-step guide: [Install and Configure BAM (Business Activity Monitoring) in a Multi-Computer Environment](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)

It is easier to understand BAM, the installation and configuration process, and dependencies by splitting into three BizTalk Server environments described in the following table:

| Runtime Environment | Design-time Environment | Usage-time Environment |
|---|---|---|
| A basic BizTalk Server runtime environment can include the following servers: <ul><li>BizTalk Server</li><li>SQL Server</li><li>BizTalk BAM Server</li><li>Web Server</li></ul> | There are three roles involved during the BAM development and deployment process. Roles include: <ul><li>Business analyst</li><li>Business administrator</li><li>Application developer</li></ul> | After a BAM solution is implemented and deployed, business end users can view the reports generated by various reporting tools. These tools include: <ul><li>BAM Portal </li><li>SQL Server Reporting Services</li><li>Microsoft PerformancePoint Monitoring Server</li><li>Custom BAM reporting applications</li></ul> |

The following table describes the BAM components to install:

|Category |BAM Component|Purpose|
|---|---|---|
| Portal Components | Business Activity Monitoring | Selecting the Business Activity Monitoring component installs the software that gives business users a real-time view of their heterogeneous business processes, enabling them to make important business decisions. |
| Additional Software | BAM Alerts | Installs the necessary software that enables BizTalk Server to provide Business Activity Monitoring (BAM) alerts. <br/><br/>BAM Alerts on BizTalk Server 2013 R2 and newer use SQL Server Database Mail. SQL Notification Services is not used or supported.<br/><br/>BAM Alerts on BizTalk Server 2013 with SQL Server 2012 uses SQL Notification Services. BAM Alerts on BizTalk Server 2013 with SQL Server 2008 R2 uses SQL Notification Services. |
| | BAM Client | Selecting the BAM Client component installs the necessary client-side software that allows business users to work with the Business Activity Monitoring feature of BizTalk Server. | 
| | BAM-Eventing | Select the BAM-Eventing Support component installs the software for the BAM-Eventing Interceptors for Windows Workflow Foundation and Windows Communication Foundation. Selecting this component also installs the BAM Event API that is used to send events to the BAM database from custom applications. BAM-Eventing Support is part of the Business Activity Monitoring feature in BizTalk Server. | 

### Configure BAM
Step-by-step guide: [Install and Configure BAM (Business Activity Monitoring) in a Multi-Computer Environment](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)

Open BizTalk Server Configuration and choose [Custom Configuration](configure-biztalk-server.md). In Custom Configuration, you can configure advanced options and selectively configure or unconfigure each feature. 

### Install and Configure SQL Server for BAM

In [What's New, Installation, Configuration, and Upgrade](biztalk-server-what-s-new-installation-configuration-and-upgrade.md), you can: 

- See the supported software requirements for BizTalk Server, including the supported SQL Server versions
- Install the prerequisite software, including SQL Server. For SQL Server-specific installation steps, see [Install SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) or [Install SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).

In addition to Database Services that required by the BizTalk Server core functions, BAM also requires the following:

- SQL Server Analysis Services (SSAS)

- SQL Server Integration Services (SSIS)

- SQL Server Database Mail or SQL Server Notification Services (SSNS)

##### Configure SSIS
If your SQL Server is installed on a computer other than the BizTalk Server, then configure SSIS. In this task, you configure the SSIS to use the msdb database on a remote SQL Server.

1. Open a Command Prompt.

2. Change directory to %ProgramFiles%\Microsoft SQL Server\100\DTS\Binn.

3. Run the following command: notepad MsDtsSrvr.ini.xml

4. In Notepad, update the text inside the “<ServerName>” tag to the host name of the SQL Server. Save your changes.

5. From the Command Prompt, execute the following command: net stop MsDtsServer

6. From the Command Prompt, execute the following command: net start MsDtsServer

    **Additional**:  
    By default, the Integration Services service is configured to manage packages that are stored in the msdb database in a local, default instance of Database Engine. To manage packages that are stored in a named instance or a remote instance of the Database Engine, or in multiple instances of the Database Engine, modify the configuration file. For example, you can create more root folders of the type, SqlServerFolder, to manage packages in the msdb database of multiple instances of the Database Engine.If the service stops, you can also modify the configuration file to allow packages to continue running. This option displays more root folders in Object Explorer, or specifies a different folder or more folders in the file system managed by Integration Services service.

    The `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTS\ServiceConfigFile` registry key specifies the location and name for the configuration file that Integration Services service uses. The default value of the registry key is C:\Program Files\Microsoft SQL Server\100\DTS\Binn\ MsDtsSrvr.ini.xml. You can update the value of the registry key to use a different name and location for the configuration file.

#### Configure BAM databases
You can configure BAM Primary Import, BAM Archive, BAM Star Schema, BAM Analysis, and BAM Notification Services Application databases on different computers. The following are the software requirements when SQL Server is installed on a computer other than the BizTalk Server:

| BAM feature | Feature configuration | BizTalk Server | SQL Server | 
|---|---|---|---|
|BAM Tools | BAM Primary Import Tables and BAM Archive database | ADOMD.NET SQL Server Integration Services | Supported SQL Server version. See [What's New, Installation, Configuration, and Upgrade](biztalk-server-what-s-new-installation-configuration-and-upgrade.md).|
| BAM Tools| Enable Analysis Services for BAM aggregations| SQL Server Integration Services| SQL Server Analysis Services| 
| BAM Notification Services Application Database| BAM Alerts| BAM Alerts <br/>Requirements listed in [What's New, Installation, Configuration, and Upgrade](biztalk-server-what-s-new-installation-configuration-and-upgrade.md).| If using SQL Server 2012 or SQL Server 2014, configure SQL Server Database Mail. If using SQL Server 2008 R2, install SQL Server 2005 Notification Services Engine Components.<br/><br/>The BAM Alerts requirements are documented at Preparing Your Computer for Installation.

> [!NOTE] 
> The service account used for the OLAP service should have db_datareader permissions on the BAM Star Schema database.

##### Notification Services – BizTalk 2013 / SQL Server 2008 R2 Only

> [!IMPORTANT]
> This section only applies if SQL Server 2008 R2 is used.

You can install SQL Server Notification Services in a multicomputer environment where the Provider, Generator, and Distributor roles of Notification Services are on different computers. The following describes the dependencies in that scenario:

- The AggregationEventProvider.dll should be installed on the computer that hosts the Provider role. This .dll file is installed when you install the BAM Alerts Aggregate Event Provider during the installation of BizTalk Server. The BAM Alerts Aggregate Event Provider is present if the BizTalk Runtime, Administration Tools, or Developer Tools and SDK are installed.

- EmailNotification.xslt and FileNotification.xslt are required on the computer that hosts the Distributor role. You can copy the files in the following path from an existing BizTalk Server: \Program Files\Microsoft BizTalk Server *version*\Tracking

- Update the Notification Services Application definition file (.adf file) with the exact location of the .xslt files on the computer that hosts the Distributor role. 

**Update the Application definition file (.adf file)**:  

1. On the computer where BizTalk Server is installed, open the Notification Services command prompt.
2. Browse to \Program Files\Microsoft BizTalk Server *version*\Tracking.
3. Execute ProcessBamNsFiles.vbs to create the initial .adf file.
4. Modify the .adf file with the path to the .xslt file.
5. Execute ProcessBamNsFiles.vbs again to update the .adf file.
6. Restart the BAMAlerts NT service.

##### BAM Scale-Out Alerts Topology
If you are upgrading your existing BAM scale-out alerts topology to BizTalk Server 2013, then do the following steps on each server:

1. Stop the Notification Service and then unregister an instance of Notification Service:
    1. In **Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.
    1. At the command prompt, type: `net stop NS$<instance_name>`. For example, type: `net stop NS$BamAlerts`.
    1. To unregister the instance, type the following command: `nscontrol unregister -name BamAlerts`. 

        Unregistering an instance removes the registry entries, removes the NS$instance_name service (if present), and deletes the performance counters for the service.

2. Upgrade your servers that have Notification Services instances to a higher edition of SQL Server 2005 Notification Services.

3. To migrate your BAM databases based on the SQL Server version you are upgrading from, run the migration database command bm.exe program located in the BizTalk Server Tracking folder. For example, if SQL Server 2005 is upgraded to SQL Server 2008 R2, run the following in the command prompt with administrative credentials: `bm.exe migrate-sql –From:sql2005 –To:sql2008 –NSUser:<username>`.

4. Reregister the Notification Service on all the servers except the server where the migration program (bm.exe) is being used.

   1. In **Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.
   2. At the command prompt, type: `nscontrol register -name BamAlerts -server <NS DB Server> -service -serviceusername "<NSServiceUserName>" -servicepassword "<NSServicePassword>"`

      This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service computer by nscontrol).

      > [!IMPORTANT] 
      > Remember to use the new Notification Services database server in the -server option when re-registering the service. In addition, use the same user name for the new Notification Services service as the old one.

5. Validate the BAM alerts: Open the **Notification Services Command Prompt** and type: `nscontrol.exe status –name BAMAlerts –server <NS DB Server>`.

### BAM Portal
The Portal Components are a set of services used by business people to communicate, collaborate, and make decisions that enable them to interact, configure, and monitor business processes and workflows. To use this feature, install Internet Information Services (IIS). The IIS requirements are in [What's New, Installation, Configuration, and Upgrade](biztalk-server-what-s-new-installation-configuration-and-upgrade.md).

### BAM Add-in from Excel
[Add or remove add-ins](https://support.office.com/article/add-or-remove-add-ins-0af570c4-5cf3-4fa9-9b88-403625a0b460) lists the steps for Excel. The BAM add-in name is **Business Activity Monitoring**.

### Configure Multiple BizTalk Groups to use a Single BAM Database
Share the BAM databases across multiple BizTalk groups:

1. Configure the first BizTalk group with the BAM features. These features include BAM tools, the BAM Analysis database, BAM alerts, and the BAM portal.

2. Configure the subsequent BizTalk groups and do the following in the BizTalk Server Configuration Wizard:

   1. Select **BAM Tools**, and then select the **Enable Business Activity Monitoring tools** and **Enable Analysis Services for BAM aggregations** check boxes.

   2. Change the **Server Name** and **Database Name** of the BAM data stores to match the same names used when configuring the first BizTalk group.

   3. Select **BAM Alerts** and then select **Enable BAM alerts**.

   4. Change the service account for BAM Alerts so it's a blank user name and password.

   5. Change the BAM Alerts SMTP Server, BAM Alerts File Location, SQL Server for Alerts Database, and Prefix for Alerts Database Names to match the same names used when configuring the first BizTalk group.

      > !NOTE] 
      > The same Primary Import Tables (PIT) can be used but with different BAM Archive, BAM Analysis, and Star Schema databases. However, this option impacts all groups that use the same PIT.

3. Select **BAM Portal**, and then select the **Enable BAM Portal** check box.

    > [!NOTE]
    > All the fields on this screen are read-only because there is a one-to-one relationship between the BAM Primary Import database and the BAM portal. Multiple BizTalk groups share the BAM portal when configured against the same BAM databases.

4. Select **Apply Configuration**.

### BAM Client Software Requirements
- For the web client, you need Internet Explorer and Office Web Components 11 version 4.0 or later.

- If you are running the web client and using SQL Server 2008 R2 Analysis Services, install Microsoft SQL Server 2008 R2 Analysis Services 10.0 OLE DB Provider. 

- For the Excel client, you need Microsoft Excel and the BAM Excel Add-in provided with BizTalk Server.


## Groups and Service Accounts
Manually create all of the domain groups and accounts before you configure BizTalk Server in a multicomputer installation. The following information is useful in creating these groups and accounts.

In a multicomputer environment, BizTalk Server supports only domain groups and domain service accounts. 

- BizTalk Server supports only <NetBIOSDomainName>\<User> name formats for Windows groups and service accounts.

- BizTalk Server supports only Active Directory domain groups and user accounts in multicomputer configurations. Domain groups include Domain Local groups, Global groups, and Universal groups, which are supported in both single computer and multicomputer environments.

- In general, Domain Local Groups are not recommended because their use requires that all of the servers, including SQL Servers, in the BizTalk Server infrastructure belong to the same domain. This consideration does not apply to small networks where all of the servers and user accounts reside in a single domain. [Active Directory groups](http://technet.microsoft.com/library/cc733001.aspx) provides more information.

- Built-in accounts such as NT AUTHORITY\LOCAL SERVICE, NT AUTHORITY\NETWORK SERVICE, NT AUTHORITY\SERVICE, NT AUTHORITY\SYSTEM, and Everyone are not supported when you install and configure BizTalk Server in a multicomputer environment.

- The user that runs the BizTalk Server configuration must belong to the following user groups: the Administrators group on the local computer, the System Administrators group on the SQL Server computer, the domain group used for the BizTalk Server Administrators group, and the domain group used for the SSO Administrators group.

- Whenever possible, use the default account names created during setup. The BizTalk Server setup program automatically configures installed components to use the default accounts. Using the default names simplifies setup and configuration, but it is not always possible. For example, there can be multiple BizTalk Server groups within an Active Domain forest. In this situation, the account names must be modified to avoid conflicts. Or, your organization might use naming standards for service and user accounts so you change the default accounts to conform to the standard.

### Windows Groups
The following table lists the Windows groups and their membership used by BizTalk Server. It also identifies the SQL Server Roles or Database Roles for the group.

| Group | Group Description | Membership | SQL Server Roles or Database Roles | 
| ---|---|---|---|
| SSO Administrators | Administrator of the Enterprise Single Sign-On (SSO) service. [Specify SSO Administrator and Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md) has more information. | Contains service accounts for Enterprise Single Sign-On service. Contains users/groups that need to be able to configure and administer BizTalk Server and SSO service.Contains accounts used to run BizTalk Configuration Manager when configuring SSO master secret server. | **db_owner** SQL Server Database Role for the SSO <br/><br/>**securityadmin** SQL Server Role for the SQL Server where SSO is located. |
| SSO Affiliate Administrators | Administrators of certain SSO affiliate applications. Can create/delete SSO affiliate applications, administer user mappings, and set credentials for affiliate application users. | Contains no service accounts. Contains account used for BizTalk Server Administrators.| |
|BizTalk Server Administrators | Has the fewest privileges necessary to perform administrative tasks. Can deploy solutions, manage applications, and resolve message processing issues. To perform administrative tasks for adapters, receive and send handlers, and receive locations, the BizTalk Server Administrators must be added to the Single Sign-On Affiliate Administrators. See [Manage BizTalk Server Security](../core/managing-biztalk-server-security.md). | Contains users/groups that need to be able to configure and administer BizTalk Server. | **BTS_ADMIN_USERS** SQL Server Database Role in the following databases:<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport<br/><br/>**db_owner** SQL Server Database Role for the following databases:<br/>BAMStarSchema<br/>BAMPrimaryImport<br/>BAMArchive<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**NSAdmin** SQL Server Database Role in the following databases: <br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>SQL Server Database Role in the following databases: <br/>BizTalkDTADb<br/>BizTalkMgmtDb. <br/><br/>**OLAP Administrators** on the computer that hosts the BAMAnalysis OLAP database. |
| BizTalk Server Operators | Has a low privilege role with access only to monitoring and troubleshooting actions. | Contains user/groups that monitor solutions. Contains no service accounts. | **BTS_OPERATORS** SQL Server Database Role in the following databases: <br/>BizTalkDTADb<br/>BizTalkEDIDb<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb | 
| BizTalk Application Users | The default name of the first In-Process BizTalk Host Group created by Configuration Manager. Use one BizTalk Host Group for each In-Process host in your environment. Includes accounts with access to In-Process BizTalk Hosts (hosts processes in BizTalk Server, BTSNTSvc.exe). | Contains service accounts for the BizTalk In-Process host instance in the host that the BizTalk Host Group is designated for.  | **BTS_HOST_USERS** SQL Server Database Role in the following databases:<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport<br/><br/> **BAM_EVENT_WRITER** SQL Server Database Role in the BAMPrimaryImport. | 
| BizTalk Isolated Host Users | The default name of the first Isolated BizTalk Host Group created by Configuration Manager. Isolated BizTalk hosts not running on BizTalk Server, such as HTTP and SOAP. Use one BizTalk Isolated Host Group for each Isolated Host in your environment. | Contains service accounts for the BizTalk Isolated host instance in the host that the Isolated BizTalk Host Group is designated for. | **BTS_HOST_USERS** SQL Server Database Role in the following databases:<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport | 
| EDI Subsystem Users | Has access to the EDI database. | Contains service accounts for BizTalk Base EDI service. | **EDI_ADMIN_USERS** SQL Server Database Role in the BizTalkEDIDb. | 
| BAM Portal Users | Has access to BAM Portal website. | Everyone group is used for this role by default. Contains no service accounts. |  | 
| BizTalk SharePoint Adapter Enabled Hosts | Has access to Windows SharePoint Services Adapter Web Service. | Contains service accounts for the BizTalk host instance to use the SharePoint Adapter. |  | 
| BizTalk B2B Operators Group | A BizTalk role that reduces the onus on the Administrators to perform all Party management operation. This role allows windows users associated with the role to perform all party management operations. | Contains users/groups that must be able to configure and administer BizTalk Server TPM data and monitor solutions. | **BTS_OPERATORS** SQL Server Database Role in the following databases: <br/>BizTalkDTADb<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BAMPrimaryImport |

### User and Service Accounts
The following table lists the Windows user or service accounts and group affiliations used by BizTalk Server. It also identifies the SQL Server Roles or Database Roles for the accounts.


|                  User                  |                                                                                                                   User Description                                                                                                                   |                  Group Affiliation                   |                                                                                SQL Server Roles or Database Roles                                                                                |
|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Enterprise Single Sign-On Service    |                                                                           Service account used to run Enterprise Single Sign-On Service, which accesses the SSO database.                                                                            |                  SSO Administrators                  |                                                                                                                                                                                                  |
|     BizTalk Host Instance Account      |                                                                                       Service account used to run BizTalk In-Process host instance (BTNTSVC).                                                                                        |              BizTalk Application Users               |                                                                                                                                                                                                  |
| BizTalk Isolated Host Instance Account |                                                                                       Service account used to run BizTalk Isolated host instance (HTTP/SOAP).                                                                                        |          BizTalk Isolated Host UsersIIS_WPG          |                                                                                                                                                                                                  |
|       Rule Engine Update Service       |                                               Service account used to run Rule Engine Update Service, which receives notifications to deployment/undeployment policies from the Rule engine database.                                                |                                                      |                                                              **RE_HOST_USERS** SQL Server Database Role in the BizTalkRuleEngineDb.                                                              |
|     BAM Notification Services User     |                                                                               Service account used to run BAM Notification Services, which accesses the BAM databases.                                                                               | SQLServer2005NotificationServicesUser$<ComputerName> | **NSRunService** SQL Server Database Role in the following databases:<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**BAM_ManagementNSReader** SQL Server role for the BAMPrimaryImport. |
|    BAM Management Web Service User     | User account for BAM Management Web service (BAMManagementService) to access various BAM resources. BAM Portal calls BAMManagementService with the user credentials logged on the BAM Portal to manage alerts, get BAM definition XML and BAM views. |                       IIS_WPG                        | **NSSubscriberAdmin** SQL Server Database Role in the following databases:<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**BAM_ManagementWS** SQL Server role for the BAMPrimaryImport.  |
|      BAM Application Pool Account      |                                                                                     Application pool account for BAMAppPool, which hosts the BAM Portal website.                                                                                     |                       IIS_WPG                        |                                                                                                                                                                                                  |

> [!IMPORTANT]
> For more information about Windows groups and service accounts used in BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).

## Databases list
The following is the list of SQL Server databases used in BizTalk Server:

| Data store name | Default database name | Volume | Growth | Description | 
| ---|---|---|---|---|
| SSO Database | SSODB | Low | Low | This Enterprise Single Sign-On credential database securely stores the user name and password.| 
| BizTalk Management Database | BizTalkMgmtDb | Low | Low | This database is the central meta-information store for all instances of BizTalk Server.| 
| BizTalk MessageBox Database | BizTalkMsgBoxDb | High | Medium | The BizTalk Server engine uses this database for routing, queuing, instance management, and various other tasks.<br/><br/>**Note**<br/>Auto Update Statistics, Auto Create Statistics, and the Parallelism setting are purposely turned off in the SQL Server database instance that hosts the BizTalk Server BizTalkMsgBoxDB database. Do not enable these settings. | 
| BizTalk Tracking Database | BizTalkDTADb | High | High | This database stores business and health monitoring data tracked by the BizTalk Server tracking engine. | 
| Rule Engine Database | BizTalkRuleEngineDb | Low | Low | This database is a repository for policies, which are sets of related rules and vocabularies. Vocabularies are collections of user-friendly, domain-specific names for data references in rules. | 
| BAM Primary Import Database | BAMPrimaryImport | Medium | Medium | This database collects raw BAM tracking data. | 
| BAM Archive Database | BAMArchive | Medium | Medium | This database archives old business activity data. Create a BAM Archive database to minimizes the accumulation of business activity data in the BAM Primary Import database. | 
| BAM Star Schema Database | BAMStarSchema | Medium | Medium | This database contains the staging table, and the measure and dimension tables. | 
| BAM Notification Services Application database | BAMAlertsApplication | Medium | Medium | This database contains alert information for BAM notifications. For example, when you create an alert using the BAM portal, entries are inserted in this database that specify the conditions and events to which the alert pertains, as well as other supporting data for the alert. | 
| BAM Notification Services Instance database | BAMAlertsNSMain | Medium | Medium | This database contains instance information that specifies how the notification services connect to the system that BAM is monitoring. | 

#### SQL Server databases used by SharePoint

| Data store name | Default database name | Volume | Growth | Description | 
|---|---|---|---|---|
| Windows SharePoint Services configuration database | User-defined | Low | Low | This database contains all of the global settings for the server. | 
| Windows SharePoint Services content database | User-defined | Medium | Medium | This database contains all of the site content, such as list items and documents. | 

## Install BizTalk a multi-server environment

1. **Install Active Directory Domain Services** - The first step required to install BizTalk Server into a multiple server environment is to install Active Directory domain services for the various BizTalk Server groups and accounts. To create the Active Directory domain, refer to the following:

   - Windows Server 2012 and newer: [Install Active Directory Domain Services](https://docs.microsoft.com/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-)
   - Windows Server 2008 R2: [AD DS Installation and Removal Step-by-Step Guide](https://technet.microsoft.com/library/cc755258(WS.10).aspx)

     > [!IMPORTANT]
     > The BizTalk Server groups described in the **User and Service Accounts Used In BizTalk Server** table (in this topic) must be created before installing BizTalk Server into a multiple server environment.

2. **Install Multiple Instances of SQL Server as needed** – If your load requirements dictate that you need multiple MessageBox databases or that you need to spread the BizTalk Server I/O load over multiple SQL Server instances, then install more SQL Server instances as required. 

    For more information about performance testing your BizTalk Server environment, and database optimization, see the [BizTalk Server Performance Optimizations Guide](../technical-guides/biztalk-server-2013-performance-optimization-guide.md). 

3. **Install Multiple BizTalk Server computers into your BizTalk Server Group as needed** – If your load requirements dictate that you need multiple BizTalk Server computers into your BizTalk Server group, then use the BizTalk Server Enterprise Edition to scale out your processing requirements across multiple BizTalk Servers. 

    > [!IMPORTANT]
    > Many of the Enterprise level features of BizTalk Server such as clustering, adding multiple servers to a group, and native 64-bit processing are only available with the Enterprise edition of BizTalk Server.

4. **Install Cumulative Updates** - Cumulative updates are listed in Windows Update. [KB article 2555976](http://support.microsoft.com/kb/2555976) lists available service packs and cumulative updates.

## Cluster considerations

- **Clustering MSDTC** – The Microsoft Distributed Transaction Coordinator (MSDTC) is a central component of any BizTalk Server environment. If other components of the BizTalk Server environment are clustered, it is recommended to also cluster MSDTC. 

- **Install SQL Server Failover Clustering** – To provide high availability/fault tolerance for the BizTalk Server databases, it is recommended that the BizTalk Server databases are installed on a SQL Server failover cluster. For information on installing SQL Server failover cluster, see: 

  * SQL Server 2016: [Always On Failover Cluster Instances (SQL Server)](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server)
  * SQL Server 2014: [Windows Server Failover Clustering (WSFC) with SQL Server](https://msdn.microsoft.com/library/ms189134(v=sql.120).aspx)

    Once SQL Server is configured for high availability/fault tolerance, then the SQL Server clustered instance can be referenced just as any other SQL Server instance by the BizTalk Server configuration.

- **Configure the Enterprise Single Sign-On Master Secret Server as a cluster resource** – A failure of the Enterprise Single Sign-On Master Secret Server can cause a system-wide failure of the BizTalk Server environment. It is recommended to configure the Enterprise Single Sign-On Master Secret Server for high availability/fault tolerance by configuring the Master Secret Server as a cluster resource. Because the Master Secret Server is not a resource-intensive component of a BizTalk Server environment, it is recommended that the Master Secret Server be clustered on the same cluster nodes as the SQL Server instances. For more information about configuring the Enterprise Single Sign-On Master Secret Server as a cluster resource, see [Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md). 

- **Configure a BizTalk host as a cluster resource** – Running multiple instances of a BizTalk Server host provides high availability/fault tolerance. As a result, configuring a BizTalk host as a cluster resource is not recommended except in particular circumstances. For example, you can confgure a BizTalk host as a cluster resource when accommodating high availability/fault tolerance or for providing ordered delivery for certain BizTalk Server adapters. For more information about when it is appropriate to configure a BizTalk host as a cluster resource, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md). Also see [How to Configure a BizTalk Host as a Cluster Resource](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md). 

- **Cluster Message Queuing** – See [install and cluster MSMQ](https://blogs.msdn.microsoft.com/biztalknotes/2013/03/20/how-to-install-and-cluster-msmq-on-windows-server-2012/).

- **Cluster the File System** – See [How to Cluster the File System](http://go.microsoft.com/fwlink/p/?LinkId=189517).

## Use SCOM
The BizTalk Server Management Pack for Operations Manager provides comprehensive discovery and monitoring of BizTalk Server components and applications that are running in multiple machines. For more information about the BizTalk Server Management Pack, see http://www.microsoft.com/download/details.aspx?id=39617.

## Next  
[Configure BizTalk](configure-biztalk-server.md)