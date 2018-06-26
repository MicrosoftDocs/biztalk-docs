---
title: "Configuring BAM Alerts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, alerts"
  - "alerts, timeout values"
  - "Notification Services, configuration tips"
  - "alerts, configuring"
  - "managing [BAM definitions], configuring alerts"
ms.assetid: 29327466-c8e9-41e8-bc12-f3ac6b5d3096
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring BAM Alerts
Administrators can modify certain elements of the BAM alert framework. This topic describes the configuration options available to administrators.  
  
> [!NOTE]
>  When creating alerts you should be aware that time data is stored in a Local Time format on the OLAP, Star Schema, and Notification Services databases. It is also assumed that all three databases are in the same time zone. On the Primary Import database, information is stored in the UTC time format and can be in the same or different time zone.  
  
## Changing the ADF configuration  
 When deploying a view the BAM Management utility uses the CommandTimeout value specified in the bm.exe.config file to populate Notification Services application definition file \<EventRule\>\\<ActionTimeout\> element.  
  
 Changing the value of CommandTimeout in bm.exe.config does not change the CommandTimeout value for views deployed prior to the change.  
  
 The procedure below uses the ProcessBamNSFiles.vbs to obtain the configuration and the Notification Services application definition file. For more information on the script, see [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md).  
  
 How to change the ActionTimeout for NS for already deployed views:  
  
#### To change the command timeout value  
  
1.  Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  Navigate to the tracking folder by typing at the command prompt **cd “C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking”** or **cd “C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\Tracking”** on a 64 bit computer. Press **ENTER**.  
  
3.  Retrieve the ADF file. Type **cscript ProcessBamNSFiles.vbs -Get \<ConfigFilePath\> \<ADFFilePath\> \< PID Server\> \< PID database \>**. Replacing the ConfigFilePath, ADFFilePath, PID Server, and PID database with the appropriate values for your installation.  
  
4.  Press **ENTER**.  
  
5.  Open the ADF file in an editor and search for \<ActionTimeout\>, update with desired value & please note that this value is an XML duration.  
  
6.  Save the ADF file. Type **cscript ProcessBamNSFiles.vbs -Update \<ConfigFilePath\> \<ADFFilePath\> \< PID Server\> \< PID database \>**.  
  
7.  Press **ENTER**.  
  
### Notification Service configuration tips  
 If you configure BAM Alerts in such a way as to place the Alerts databases on a remote computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], then the Notification Services Database Components must be installed on the SQL Server instance. If these components are not present on the SQL instance, then configuration of BAM Alerts will fail with an error indicating that permissions could not be granted to the Notification Services Extended Stored Procedures. For more information on installing the Notification Services component, see [http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999).  
  
 BAM allows you to change the account that BAM uses to access the Notification Services. If you change this account in any way other than running NSControl, you will receive an error informing you to use the NSControl to change the account.  
  
> [!NOTE]
>  You cannot use the LocalSystem or SYSTEM accounts for installing and configuring Notification Services. These are special accounts that you cannot log on to and that you cannot use to grant file and SQL Server permissions to the BAM alerts user.  
>   
>  To install and configure Notification Services, create a new user account on the local computer, grant it all the requisite permissions, and then use it to configure Notification Services.  
  
##### To change NS user account for BAM  
  
1. Use NSControl to update the user account.  
  
2. Grant the NS user read, write, and change permissions to the BAM Alerts File Location share.  
  
3. Add the NS user as a member of NSRunService role in both the BAMAlerts instance and application databases.  
  
4. Grant the NS User rights on the local machine using the documentation at [http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005).  
  
5. Grant the NS rights to the NS database according to [http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008).  
  
6. Grant the NS user login rights to SQL server and database access to the Primary Import database.  
  
7. Add the NS user to the BAM_ManagmentNSReader SQL role.  
  
8. Add the NS user to the "BAM Alerts" role in BamAnalysis database.  
  
   If you modify the file drop location for alerts delivered by file. You must restart the SQL Notifications Services.  
  
   If the NS service is not restarted, alerts will continue being delivered to the original file drop location.  
  
   The file drop location is changed by modifying the following line of the BAM configuration file and using the BAM manangement utility update-config command.  
  
   \<Property Name="FileDropUNC"\>\\\\<computer name\>\alerts\</Property\>  
  
   For more information on the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md).