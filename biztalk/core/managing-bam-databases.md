---
description: "Learn more about: Managing BAM Databases"
title: "Managing BAM Databases"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Managing BAM Databases
Administrators use the BAM Management utility (bm.exe) to set up, manage, and update the BAM databases. This section shows you how to use the BAM Management utility to perform these common administrator tasks for the BAM databases, which are described in the following table.  
  
 For information about backing up and restoring the BAM databases, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).  
  
|Database|Default database name|Description|  
|--------------|---------------------------|-----------------|  
|BAM Primary Import database|BAMPrimaryImport|Where BAM collects raw tracking data.|  
|BAM Notification Services Application database|BAMAlertsApplication|Contains alert information for BAM notifications. For example, when you create an alert using the BAM portal, entries are inserted in the database specifying the conditions and events to which the alert pertains, as well as other supporting data items for the alert.|  
|BAM Notification Services Instance database|BAMAlertsNSMain|Contains instance information specifying how the notification services connect to the system that BAM is monitoring.|  
|BAM Star Schema database|BAMStarSchema|Contains the staging table, and the measure and dimension tables.|  
|BAM Analysis database|BAMAnalysis|Contains BAM OLAP cubes for both online and offline analysis.|  
|BAM Archive database|BAMArchive|Archives old business activity data. You can create a BAM Archive database to minimize the accumulation of business activity data in the BAM Primary Import database.|  
  
## In This Section  
  
-   [Archiving Primary Import Database Data](../core/archiving-primary-import-database-data.md)  
  
-   [Creating a Partitioned View in the Archiving Database](../core/creating-a-partitioned-view-in-the-archiving-database.md)  
  
-   [Scheduling SQL Server Integration Services Packages](../core/scheduling-sql-server-integration-services-packages.md)  
  
-   [How to Set Up the BAM Databases Using the BAM Management Utility](../core/how-to-set-up-the-bam-databases-using-the-bam-management-utility.md)  
  
-   [How to Retrieve the BAM Configuration File Using the BAM Management Utility](../core/how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility.md)  
  
-   [How to Update the BAM Configuration Using the BAM Management Utility](../core/how-to-update-the-bam-configuration-using-the-bam-management-utility.md)  
  
-   [How to Reference Additional BAM Primary Import Databases](../core/how-to-reference-additional-bam-primary-import-databases.md)  
  
-   [How to Disable a BAM Primary Import Database Reference](../core/how-to-disable-a-bam-primary-import-database-reference.md)  
  
-   [How to List All Referenced Databases](../core/how-to-list-all-referenced-databases.md)  
  
-   [How to Remove Incomplete Activity Instances](../core/how-to-remove-incomplete-activity-instances.md)  
  
-   [How to Update the BAM Management Utility Configuration After a Backup and Restore](../core/update-the-bam-management-utility-configuration-after-a-backup-and-restore.md)  
  
-   [How to Integrate BAM with SQL Server Reporting Services](../core/how-to-integrate-bam-with-sql-server-reporting-services.md)  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)
