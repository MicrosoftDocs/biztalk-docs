---
title: "Databases in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Notification Services Application database [BAM]"
  - "Archive database [BAM]"
  - "Analysis database [BAM]"
  - "Windows SharePoint Services, content database"
  - "Windows SharePoint Services, configuration database"
  - "TPM database"
  - "BizTalk Server, databases"
  - "Notification Services Instance database [BAM]"
  - "Star Schema database [BAM]"
  - "Primary Import database [BAM]"
  - "Rule Engine database"
  - "databases, BizTalk Server"
  - "SSO database"
  - "Tracking Analysis Server database [BAM]"
  - "Management database"
  - "Tracking database"
  - "MessageBox database"
ms.assetid: bb504a26-cae6-4f2a-9b86-3554ef8f6045
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Databases in BizTalk Server
Microsoft BizTalk Server installs several databases in SQL Server. This topic describes these databases, and the SQL logic groups used by these databases.  

## Database descriptions
The following table describes the typical usage characteristics for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
BizTalk Server runtime operations typically use the first four databases: BizTalk Server Management database, MessageBox databases, Tracking database, and SSO database. Depending on the BizTalk Server functionality that you use, you may have some or all of the other databases in the table.  
  
|Database|Default database name|Description|  
|--------------|---------------------------|-----------------|  
|BAM Analysis|BAMAnalysis|This database contains Business Activity Monitoring (BAM) OLAP cubes for both online and offline analysis.|  
|BAM Archive|BAMArchive|This database archives old business activity data. Create a BAM Archive database to minimize the accumulation of business activity data in the BAM Primary Import database.|  
|BAM Notification Services Application database|BAMAlertsApplication|This database contains alert information for BAM notifications. For example, when you create an alert using the BAM portal, entries are inserted in the database specifying the conditions and events to which the alert pertains, as well as other supporting data items for the alert.|  
|BAM Notification Services Instance database|BAMAlertsNSMain|This database contains instance information specifying how the notification services connect to the system that BAM is monitoring.|  
|BAM Primary Import database|BAMPrimaryImport|This is the database where BAM collects raw tracking data.|  
|BAM Star Schema|BAMStarSchema|This database contains the staging table, and the measure and dimension tables.|  
|BizTalk Management database|BizTalkMgmtDb|This database is the central meta-information store for all instances of BizTalk Server.|  
|BizTalk MessageBox database|BizTalkMsgBoxDb|This database is used by the BizTalk Server engine for routing, queuing, instance management, and a variety of other tasks.|  
|BizTalk Tracking database|BizTalkDTADb|This database stores health monitoring data tracked by the BizTalk Server tracking engine.|  
|Rule Engine database|BizTalkRuleEngineDb|This database is a repository for:<br /><br /> -   Policies, which are sets of related rules.<br />-   Vocabularies, which are collections of user-friendly, domain-specific names for data references in rules.|  
|SSO database|SSODB|This Enterprise Single Sign-On database securely stores the configuration information for receive locations.|  
|Windows SharePoint Services configuration database|*User-defined*|This database contains all of the global settings for the server.|  
|Windows SharePoint Services content database|*User-defined*|This database contains all of the site content, such as list items and documents.|  

## Database login accounts

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates SQL login groups, and maps them to the SQL Server roles and database roles listed in the following table:  
  
|Group|Description|SQL Server Roles or Database Roles|  
|-----------|-----------------|----------------------------------------|  
|BizTalk Application Users|Includes all accounts with access to In-Process BizTalk hosts (hosts processes in BizTalk Server, BTSNTSvc.exe).  Use one BizTalk Host Group for each In-Process host in your environment.|BTS_HOST_USERS SQL Server Database Role in the following databases:<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> BAM_EVENT_WRITER SQL Server Database Role in the BAMPrimaryImport|  
|BizTalk Isolated Host Users|Includes all accounts with access to the Isolated BizTalk hosts. Use one BizTalk Isolated Host Group for each Isolated Host in your environment.|BTS_HOST_USERS SQL Server Database Role in the following databases:<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport|  
|BizTalk Server Administrators|Includes all BizTalk Server Administrators that will deploy solutions, manage applications and resolve message processing issues.|BTS_ADMIN_USERS SQL Server Database Role in the following databases:<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> db_owner SQL Server Database Role for the following databases:<br /><br /> BAMStarSchema<br /><br /> BAMPrimaryImport<br /><br /> BAMArchive<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> NSAdmin SQL Server Database Role in the following databases:<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BizTalkDTADb<br /><br /> BizTalkMgmtDb<br /><br /> OLAP Administrators on the computer hosting the BAMAnalysis OLAP database.|  
|BizTalk Server Operators|Has a low privilege role with access only to monitoring and troubleshooting actions<br /><br /> Contains no service accounts|BTS_OPERATORS SQL Server Database Role in the following databases:<br /><br /> BizTalkDTADb<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb|  
|SSO Administrators|Top-level administrators of the Enterprise Single Sign-On (SSO) service.<br /><br /> Contains user account used to run BizTalk Configuration must be in this group.<br /><br /> Contains Enterprise Single Sign-On Service account and any users/groups that need to be able to configure and administer BizTalk Server and SSO.|db_owner SQL Server Database Role for the SSO<br /><br /> securityadmin SQL Server Role for the SQL Server where SSO is located|  

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates SQL login accounts, and maps them to the SQL Server database roles listed in the following table:  
  
|User Account|Description|SQL Database Roles|  
|------------------|-----------------|------------------------|  
|Rule Engine Update Service|User account used to the Rule Engine Update Service.|RE_HOST_USERS SQL Server Database Role in the BizTalkRuleEngineDb|  
|BAM Notification Services User|User account used to the BAM Notification Services.|NSRunService SQL Server Database Role in the following databases:<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAM_ManagementNSReader SQL Server Database role for the BAMPrimaryImport|  
|BAM Management Web Service user|User account used to the BAM Management Web Service.|NSSubscriberAdmin SQL Server Database Role in the following databases:<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAM_ManagementWS SQL Server Database role for the BAMPrimaryImport|  
  
  
## See Also  
 [Database Structure and Jobs](../core/database-structure-and-jobs.md)   
 [The MessageBox Database](../core/the-messagebox-database.md)   
 [Maintaining BizTalk Server](../technical-guides/maintaining-biztalk-server-databases.md)   
 [Scaling Your Solutions](../core/scaling-your-solutions.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)