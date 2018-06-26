---
title: "Configuring BizTalk Server Log Shipping | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcef31f7-30d1-4ada-b627-2a5c9ec7e43e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring BizTalk Server Log Shipping
You use the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up all of the databases in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] source system, except for some databases used by Business Activity Monitoring (BAM). The source system is the server or group of servers that contain live data. Because some of the BAM databases have different backup and restore requirements, these databases are backed up and restored using other methods.  
  
 Backing up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and restoring them involves the following steps:  
  
1. **Configuring the Backup BizTalk Server job**  
  
    Before you can back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must first configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job on the source system, which directs backups to be automatically written to a folder where they can then be used to restore the databases on the destination system. The destination system is the server or group of servers that will be used to restore the database backups produced by the source system. For more information about this step, see [How to Configure a Backup BizTalk Server Job](../technical-guides/how-to-configure-a-backup-biztalk-server-job.md).  
  
2. **Configuring the destination system for log shipping**  
  
    You must also configure the destination system for log shipping, which provides standby server capabilities and reduces downtime in the event of a system failure. For more information about this step, see [How to Configure the Destination System](../technical-guides/how-to-configure-the-destination-system.md).  
  
3. **Restoring the databases**  
  
    When a hardware failure occurs, you can restore your databases by using the backups and logs sent to your destination system. For more information about this step, see [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).  
  
## BizTalk Server Databases  
 The following tables describe the databases used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and identify which methods are used to back up the databases.  
  
### Databases Backed Up by the Backup BizTalk Server Job  
 The following table lists the databases that are backed up and restored as a part of the Backup BizTalk Server job. You can modify the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up custom databases by adding them to the adm_OtherBackupDatabases table. For more information, see [How to Back Up Custom Databases](http://go.microsoft.com/fwlink/?LinkID=151569) (<http://go.microsoft.com/fwlink/?LinkID=151569>).  
  
|Database|Default database name|Description|  
|--------------|---------------------------|-----------------|  
|BAM Primary Import database|BAMPrimaryImport|This is the database where the Business Activity Monitoring (BAM) collects raw tracking data.|  
|BAM Notification Services Application database|BAMAlertsApplication|This database contains alert information for BAM notifications. For example, when you create an alert using the BAM portal, entries are inserted in the database specifying the conditions and events to which the alert pertains, as well as other supporting data items for the alert.|  
|BAM Notification Services Instance database|BAMAlertsNSMain|This database contains instance information specifying how the notification services connect to the system that BAM is monitoring.|  
|BizTalk Tracking database|BizTalkDTADb|This database stores health monitoring data tracked by the BizTalk Server tracking engine.|  
|BizTalk Management database|BizTalkMgmtDb|This database is the central meta-information store for all instances of BizTalk Server.|  
|BizTalk MessageBox database|BizTalkMsgBoxDb|This database is used by the BizTalk Server engine for routing, queuing, instance management, and a variety of other tasks.|  
|Rule Engine database|BizTalkRuleEngineDb|This database is a repository for:<br /><br /> -   Policies, which are sets of related rules.<br />-   Vocabularies, which are collections of user-friendly, domain-specific names for data references in rules.|  
|SSO database|SSODB|This Enterprise Single Sign-On database more securely stores the configuration information for receive locations.|  
  
### Databases Backed Up When Backing Up the BAM Analysis and Tracking Analysis Server Databases  
 The following table lists the databases that are backed up using the procedures in [Backing Up the BAM Analysis and Tracking Analysis Server Database](http://msdn.microsoft.com/library/aa578580\(v=bts.70\).aspx):  
  
|Database|Default database name|Description|  
|--------------|---------------------------|-----------------|  
|BAM Star Schema|BAMStarSchema|This database contains the staging table, and the measure and dimension tables.|  
|BAM Analysis|BAMAnalysis|This database contains BAM OLAP cubes for both online and offline analysis.|  
|BAM Archive|BAMArchive|This database archives old business activity data. Create a BAM Archive database to minimize the accumulation of business activity data in the BAM Primary Import database.|  
|Tracking Analysis Server|BizTalkAnalysisDb|This database stores health monitoring online analytical processing (OLAP) cubes.|  
  
 This section of the operations guide describes additional steps that you should follow to configure BizTalk Server log shipping.  
  
## In This Section  
  
-   [Configuring the Source System](../technical-guides/configuring-the-source-system.md)  
  
-   [How to Configure the Destination System](../technical-guides/how-to-configure-the-destination-system.md)  
  
-   [Configuring BizTalk Server Log Shipping for Additional Databases](../technical-guides/configuring-biztalk-server-log-shipping-for-additional-databases.md)  
  
-   [Monitoring BizTalk Server Log Shipping](../technical-guides/monitoring-biztalk-server-log-shipping.md)