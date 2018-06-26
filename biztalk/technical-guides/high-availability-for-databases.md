---
title: "High Availability for Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63813d87-1ce4-4645-bb2a-d55e413fcace
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# High Availability for Databases
BizTalk Server relies heavily on SQL Server for data store and data persistence. All other components and hosts in BizTalk Server have specific roles in the process of integrating disparate business applications (for example, receiving, processing, or routing messages), but the database computer captures this work and persists it to disk. For example, when BizTalk Server receives an incoming message, the receive host persists it to the MessageBox database before other hosts retrieve the message for orchestration processing and sending. If your BizTalk solution involves orchestration, BizTalk Server routes the message to the host that executes the business process (processing host), and saves the message to the MessageBox database after the orchestration finishes. The sending host then retrieves the message from the database before sending it to the external application through the appropriate send adapter.  
  
 To provide high availability for the BizTalk Server databases, use Windows Clustering to configure two or more computers that are running SQL Server to create a server cluster. This server clustering provides redundancy and fault tolerance for the BizTalk Server databases. Unlike load-balanced clustering, where a group of computers functions together to increase availability and scalability, server clustering typically involves a pair of database computers in an active/passive configuration so that one computer provides backup resources for the other.  
  
 The following figure shows a BizTalk Server database tier with high availability through active/passive server clustering.  
  
 ![BizTalk Server Database Tier](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 If the active database computer encounters errors or fails, the passive computer becomes active and assumes control over the database resources until the failed computer is repaired. The database service fails over and restores data connections to the new active computer and enables the BizTalk application to continue functioning.  
  
## BizTalk Server Databases  
 Microsoft BizTalk Server installs several databases in SQL Server. The following table shows typical usage characteristics for the BizTalk Server databases.  
  
|Database|Default database name|Usage characteristics|  
|--------------|---------------------------|---------------------------|  
|Management database|BizTalkMgmtDb|This database handles low-usage read and write operations.|  
|MessageBox database|BizTalkMsgBoxDb|This database handles high-usage read and write operations.|  
|Tracking database|BizTalkDTADb|This database handles potentially high-usage write operations depending on the amount of data that you configure to be tracked, and low-usage read operations.|  
|SSO database|SSODB|This database handles low-usage read and write operations.|  
|BAM Analysis database|BAMAnalysis|This SQL Server Analysis Services database handles potentially high-usage read and write operations, depending on the level of monitoring performed.|  
|BAM Star Schema database|BAMStarSchema|This SQL Server Analysis Services database handles potentially high-usage read and write operations, depending on the level of monitoring performed.|  
|BAM Primary Import database|BAMPrimaryImport|This SQL Server Analysis Services database handles potentially high-usage read and write operations, depending on the level of monitoring performed.|  
|BAM Archive database|BAMArchive|This SQL Server Analysis Services database handles potentially high-usage read and write operations, depending on the level of monitoring performed.|  
|Rule Engine database|BizTalkRuleEngineDb|This database handles potentially low-usage read and write operations, unless you update the rules.|  
|Tracking Analysis Services database|BizTalkAnalysisDb|This SQL Server Analysis Services database handles high-usage read and write operations.|  
  
 BizTalk Server runtime operations typically use the first four databases (Management database, MessageBox databases, Tracking database, and SSO database). Depending on the traffic on these databases, you can put them on separate computers that are running SQL Server. Depending on the BizTalk Server functionality that you use, you may have some or all of the other databases in the table. You can scale out and cluster these databases as needed.  
  
 Make sure that you follow good SQL Server deployment practices, such as using separate disks for each database.  
  
 For the BizTalk Server databases, we recommend that you do the following:  
  
- **Set up failover clustering**. Failover clustering enables SQL Server to automatically switch the processing for an instance of SQL Server from a failed server to a working server.  
  
   The BAM Primary Import database collects event data. In the event of a disaster, data that was written to the BAM Primary Import database since the last backup will be lost. Because there is no way to regenerate lost events, it is especially important that you enable failover clustering on your BAM Primary Import database.  
  
- **Use SQL Server RAID 1+0 (redundant array of independent disks)**, especially for the MessageBox database and the BAM Primary Import database.  
  
  For information about backing up your BizTalk Server databases, see [Best Practices for Disaster Recovery](../technical-guides/best-practices-for-disaster-recovery.md).  
  
> [!NOTE]  
>  Microsoft SQL Server provides a software solution known as database mirroring for increasing the probability that a database is available. The use of SQL Server database mirroring is not currently a supported solution for ensuring high availability of the Microsoft BizTalk Server databases because of potential problems maintaining transactional consistency in the BizTalk Server databases.  
>   
>  For more information about database mirroring and cross-database transactions in SQL Server, see [Transactions - availability groups and database mirroring](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring). BizTalk Server databases should be installed on a SQL Server cluster to ensure high availability and log shipping should be utilized for purposes of disaster recovery.  
>   
>  For more information about log shipping, see [What Is BizTalk Server Log Shipping?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## In This Section  
  
-   [Clustering the BizTalk Server Databases](../technical-guides/clustering-the-biztalk-server-databases2.md)  
  
-   [Scaling Out the BizTalk Server Databases](../technical-guides/scaling-out-the-biztalk-server-databases.md)  
  
## See Also  
 [Planning for High Availability](../technical-guides/planning-for-high-availability2.md)   
 [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [High Availability for the Master Secret Server](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [Disaster Recovery](../technical-guides/disaster-recovery.md)