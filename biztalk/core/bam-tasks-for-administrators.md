---
title: "BAM Tasks for Administrators | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d9ae9a6-50fa-4f82-8e48-8dffa55c127f
caps.latest.revision: 33
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Tasks for Administrators
This topic describes typical tasks that BAM administrators undertake in managing the BAM infrastructure.  
  
## Configuring BAM  
 The initial configuration of BAM is done using the BizTalk Server Configuration Wizard. Using the configuration wizard administrators can:  
  
- Enable Business Activity Monitoring tools  
  
- Enable SQL Server Analysis Services for BAM aggregations  
  
- Specify the server name and databases used for BAM tools  
  
- Enable SQL Server Notification Services for BAM alerts  
  
- Specify the account used to run the BAM Notification service  
  
- Specify the SMTP server that is used to send BAM alerts  
  
- Specify the file location used to store BAM alerts  
  
- Specify the name of SQL server on which the BAM alerts databases resides  
  
- Specify the prefix for alerts database names  
  
- Enable the BAM portal on a computer  
  
- Specify the Web service accounts used to run the BAM portal  
  
- Specify the Windows groups that can access the BAM portal  
  
- Specify the location of the BAM portal Web site  
  
  For more information about using the configuration wizard see the following topics:  
  
- [Configure BAM Alerts](../install-and-config-guides/configure-biztalk-server.md)  
  
- [Configure BAM Tools](../install-and-config-guides/configure-biztalk-server.md)  
  
- [Configure the BAM Portal](../install-and-config-guides/configure-biztalk-server.md)  
  
### Distributed Notification Services - SQL Server 2008 R2 only
Configuring BAM to run in a distributed environment affords performance benefits when processing alerts and notifications. When you do this, the Provider, Generator, and Distributor roles of Notification Services are on different computers and you must install Notification Services in the multiple computer environment.  

> [!NOTE]
> Starting with SQL Server 2012, BizTalk Server uses SQL Database Mail. So if you're using SQL Server 2012 or newer, this does not apply to you. See [BAM Alerts](../install-and-config-guides/prepare-your-computer-for-installation.md#BKMK_BAMAlerts) for guidance.
  
##### To configure distributed Notification Services  
  
1. Install SQL Server Notification Services. 
  
   > [!NOTE]
   >  Notification Services is not included in SQL Server. Install SQL Server Notification Services when you install BizTalk Server by selecting the **BAM Alert Provider for SQL Notification Services** option under **Additional Software** on the **Component Installation** page of the installation wizard.  
  
2. To create the BAM notification service on each computer in the distributed environment run C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol register -name bamalerts -server \<server name\> -service -serviceusername \<alertsuseraccount\> -servicepassword \<passwd\> from a command prompt.  
  
3. Edit the BAM infrastructure configuration file on each computer being configured for distributed Notifications Serviced. To get the configuration file, use the **bm.exe get-config -FileName:\<output file\>** command.  
  
4. Edit the configuration file to reference the servers in the distributed Notification services environment:  
  
   ```  
   <Property Name="GeneratorServerName">PFIDWYUK</Property>  
   <Property Name="ProviderServerName">PFIDWYUK</Property>  
   <Property Name="DistributorServerName">PFIDWYUK</Property>  
   ```  
  
5. Use the bm.exe update-config -FileName:\<config file\> to update the BAM configuration.  
  
6. Restart the Notification Services on all the computers in the distributed environment.  
  
   For more information on installing BAM in a multicomputer environment, see [Install and Configure BAM (Business Activity Monitoring) in a Multi-Computer Environment](http://go.microsoft.com/fwlink/p/?LinkID=208597).  
  
### Moving the BAM Primary Import Database  
 At some point it may become necessary to move the BAM Primary Import database, such as when you are upgrading hardware or scaling up operations. To move the database you perform a backup and restore operation. For more information about this process, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).  
  
### Working with BAM Definitions  
 Administrators work closely with BAM definitions. The primary tool you use to work with BAM definitions is the BAM Management utility. You can perform the following tasks by using this utility:  
  
- Changing activities. You can use the **deploy-all**, **update-all**, **remove-activity**, **and set-actvitywindow** commands of the BAM management utility to change your deployed activities.  
  
- Applying indexes to activity tables to enhance performance. You use the **create-index** and **delete-index** commands to modify the indexes on activities.  
  
- Setting security on views. You can use the **add-account** and **remove-account** commands to grant users access rights to views.  
  
- Configuring distributed navigation of activities. You use the **enable-reference** and **disable-reference** commands to configure distributed navigation of activities. For more information about the distributed navigation of activities, see [Managing Distributed Navigation of Remote Activities](../core/managing-distributed-navigation-of-remote-activities.md).  
  
- Auditing changes. You can list changes to the BAM dynamic infrastructure using the **get-changes** command.  
  
  For a description of all the commands available through the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md). For examples of using the BAM Management utility to work with BAM definitions, see [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md).  
  
## Configuring Multiple BizTalk Groups to Reference a Single BAM Database  
 When configuring BAM to use either a new or an existing BizTalk Server group, you can configure the group to use the same BAM databases that are already in use by another BizTalk Server group.  To configure BAM in this manner, you must perform the following tasks:  
  
-   Get the configuration information from the existing BAM Primary Import database using the BizTalk Server Configuration Wizard. This includes the server and database names. Note the state of the check boxes. Be sure to get the configuration information for both the BAM Tools and BAM Alerts pages.  
  
-   Configure BAM for the new group, and enter the exact information as configured already for the target PIT. When entering the configuration information for the new group you will use all the information collected from the existing group to configure the new group, except the BAM Alerts user, which you must leave blank.  
  
## Backing Up and Restoring BAM  
 Administrators should plan for disaster recovery situations. You should back up the BAM Analysis, Tracking Analysis, BAM Star Schema, BAM Archive, and BAM Primary Import databases to provide for situations in which you must restore them.  For information about backing up and restoring the BAM databases, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).  
  
## Working with Renamed Servers  
 When you rename a server or move the BAM infrastructure between servers, you must update the Excel workbook by updating the BAM definitions in that workbook.  
  
 The scenarios in which you would need to update the workbook include:  
  
- A staging scenario, in which you move the BAM infrastructure to a new database. To ensure that the Excel workbooks are still functional, you must redeploy or migrate and then re-update the workbooks.  
  
- A scenario in which you rename the computer running BizTalk Server. This requires updating the DTS packages and OLAP data source in addition to updating the workbook.  
  
  There are two approaches you can use to update the Excel workbook:  
  
- Run the following BAM Manager command from the new server:  
  
   **bm.exe update-livedataworkbook -Name:\<livedata workbook to update.xls\>**  
  
  > [!NOTE]
  >  You can also specify the new server name and/or BAM Primary Import database name: **bm.exe update-livedataworkbook -Name:\<livedata workbook to update.xls\> [-Server:\<server\>] [-Database:\<database\>]**  
  
- Alternatively, you can update the Excel workbook from within Excel:  
  
  1.  Open the workbook you want to update.  
  
  2.  From the BAM menu, click **BAM Db Connection**.  
  
  3.  Enter the new server name and BAM Primary Import database name.  
  
## Managing Alerts  
 Administrators can manage alerts in a several ways:  
  
 You can use the BAM Management utility to deploy and remove alerts. You can also use the utility to add and remove subscriptions, as well as to enable and disable alerts. For more information about using the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md), [Managing BAM Security](../core/managing-bam-security.md), and [Managing BAM Definitions](../core/managing-bam-definitions.md).  
  
 You can also create and remove alerts through the BAM portal.  For information about creating alerts using the BAM portal, see [Activity Searches in the BAM Portal](../core/activity-searches-in-the-bam-portal.md).  
  
### Cleaning up the Alerts Chronicle table  
 If BAM alerts are configured, a SQL job is created for each activity view that is created. The job will be named using the following template:  
  
 bam_\<View Name\>_\<Activity View\>_DelAlertHistJob  
  
 This job cleans up auditing data for the instance alerts for the specified \<Activity View\> in the Bam_Metadata_AlertChronicle table. If you have defined instance alerts on the particular activity view, a new row will be added to this table every time the alert is fired.  
  
 You can run this job manually to clean up the table or schedule it to run according to the need of your application or environment.  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)