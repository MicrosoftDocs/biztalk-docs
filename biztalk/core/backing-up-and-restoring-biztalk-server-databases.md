---
title: "Backing Up and Restoring BizTalk Server Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up [BAM]"
  - "databases, backing up"
  - "databases, restoring"
  - "backing up, restoring"
  - "backing up, databases"
  - "restoring, BAM"
  - "backing up, BAM"
  - "backing up, backup jobs"
  - "BAM, restoring"
  - "restoring, databases"
  - "restoring [BAM]"
  - "BAM, backing up"
ms.assetid: 82fc1af2-1389-4c79-80dc-f2df5656d201
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Backing Up and Restoring BizTalk Server Databases
You use the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up all of the databases in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] source system, except for some databases used by Business Activity Monitoring (BAM). The source system is the server or group of servers that contain live data. Because BAM databases have different backup and restore requirements, these databases are backed up and restored using other methods.  

 Backing up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and restoring them involves the following steps:  

1. **Configuring the Backup BizTalk Server job**  

    Before you can back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must first configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job on the source system, which directs backups to be automatically written to a folder where they can then be used to restore the databases on the destination system. The destination system is the server or group of servers that will be used to restore the database backups produced by the source system. For more information about this step, see [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md).  

2. **Configuring the destination system for log shipping**  

    You must also configure the destination system for log shipping, which provides standby server capabilities and reduces downtime in the event of a system failure. For more information about this step, see [How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md).  

3. **Restoring the databases**  

    When a hardware failure occurs, you can restore your databases by using the backups and logs sent to your destination system. For more information about this step, see [How to Restore Your Databases](../core/how-to-restore-your-databases.md).  

## BizTalk Server Databases  
 The following tables describe the databases used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and identify which methods are used to back up the databases.  

### Databases Backed Up by the Backup BizTalk Server Job  
 The following table lists the databases that are backed up and restored as a part of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job. You can modify the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up custom databases by adding them to the adm_OtherBackupDatabases table. For more information, see [How to Back Up Custom Databases](../core/how-to-back-up-custom-databases.md).  


|                    Database                    | Default database name |                                                                                                                                       Description                                                                                                                                        |
|------------------------------------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          BAM Primary Import database           |   BAMPrimaryImport    |                                                                                              This is the database where the Business Activity Monitoring (BAM) collects raw tracking data.                                                                                               |
| BAM Notification Services Application database | BAMAlertsApplication  | This database contains alert information for BAM notifications. For example, when you create an alert using the BAM portal, entries are inserted in the database specifying the conditions and events to which the alert pertains, as well as other supporting data items for the alert. |
|  BAM Notification Services Instance database   |    BAMAlertsNSMain    |                                                                            This database contains instance information specifying how the notification services connect to the system that BAM is monitoring.                                                                            |
|           BizTalk Tracking database            |     BizTalkDTADb      |                                                              This database stores health monitoring data tracked by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking engine.                                                              |
|          BizTalk Management database           |     BizTalkMgmtDb     |                                                               This database is the central meta-information store for all instances of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].                                                               |
|          BizTalk MessageBox database           |    BizTalkMsgBoxDb    |                                             This database is used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine for routing, queuing, instance management, and a variety of other tasks.                                              |
|              Rule Engine database              |  BizTalkRuleEngineDb  |                                     This database is a repository for:<br /><br /> -   Policies, which are sets of related rules.<br />-   Vocabularies, which are collections of user-friendly, domain-specific names for data references in rules.                                     |
|                  SSO database                  |         SSODB         |                                                                                       This Enterprise Single Sign-On database securely stores the configuration information for receive locations.                                                                                       |

### Databases Backed Up by the BAM Backup Process  
 The following table lists the databases that are backed up and restored using the procedures in [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md):  

|Database|Default database name|Description|  
|--------------|---------------------------|-----------------|  
|BAM Star Schema|BAMStarSchema|This database contains the staging table, and the measure and dimension tables.|  
|BAM Analysis|BAMAnalysis|This database contains BAM OLAP cubes for both online and offline analysis.|  
|BAM Archive|BAMArchive|This database archives old business activity data. Create a BAM Archive database to minimize the accumulation of business activity data in the BAM Primary Import database.|  
|Tracking Analysis Server|BizTalkAnalysisDb|This database stores health monitoring online analytical processing (OLAP) cubes.|  

## In This Section  

-   [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)  

-   [How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)  

-   [How to Restore Your Databases](../core/how-to-restore-your-databases.md)  

-   [How to Back Up and Restore SQL Agent Jobs](../core/how-to-back-up-and-restore-sql-agent-jobs.md)  

-   [How to Back Up and Restore SQL Server Logins](../core/how-to-back-up-and-restore-sql-server-logins.md)