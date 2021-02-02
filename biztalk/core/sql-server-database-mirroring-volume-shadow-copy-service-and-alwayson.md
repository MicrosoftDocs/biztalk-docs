---
description: "Learn more about: SQL Server database mirroring, Volume Shadow Copy service and AlwaysOn"
title: "SQL Server database mirroring, Volume Shadow Copy service and AlwaysOn | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b965cafc-cd34-4657-975d-0dedffd27333
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SQL Server database mirroring, Volume Shadow Copy service and AlwaysOn
Microsoft provides software solutions known as SQL Server *database mirroring* and the Windows Volume Shadow Copy Service (VSS) to increase high availability for particular scenarios. SQL Server *database mirroring* increases the probability that a database is available while the Volume Shadow Copy Service (VSS) provides backup and restore functionality for disaster recovery. The use of SQL Server *database mirroring* or the Windows Volume Shadow Copy Service are not supported solutions for ensuring high availability of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.

## Using SQL Server database mirroring to provide high availability for BizTalk Server databases
 The use of SQL Server *database mirroring* is not currently a supported solution for ensuring high availability of the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases because of potential problems maintaining transactional consistency in the BizTalk Server databases. For more information about Database Mirroring and Cross-Database Transactions in SQL Server see [https://go.microsoft.com/fwlink/?LinkId=87977](https://go.microsoft.com/fwlink/?LinkId=87977). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases should be installed on a SQL Server cluster to ensure high availability and BizTalk log shipping should be utilized for purposes of disaster recovery. For more information about BizTalk log shipping, see [Log Shipping](../core/log-shipping.md).

## Using the Volume Shadow Copy service to provide high availability for BizTalk Server databases
 The Volume Shadow Copy Service provides backup and restore functionality for disaster recovery. Because Microsoft Distributed Transaction Coordinator (MS DTC) support for VSS it is limited to local deployment and transaction coordination scenarios (and also subject to other limitations), use of the VSS service is not currently a supported solution for ensuring high availability of the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. For more information about Volume Shadow Copy Service Support with Distributed Transactions see [https://go.microsoft.com/fwlink/?LinkId=139505](https://go.microsoft.com/fwlink/?LinkId=139505).

## Using SQL Server AlwaysOn
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.

Starting with SQL Server 2016, AlwaysOn supports MSDTC transactions. As a result, the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn feature is supported when using this SQL Server version. With previous SQL Server versions, the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn feature does not support MSDTC transactions, and therefore AlwaysOn is not supported.

See [High Availability using SQL Server Always On Availability Groups](../core/high-availability-using-sql-server-always-on-availability-groups.md).

## See Also
 [Clustering the BizTalk Server Databases](../core/clustering-the-biztalk-server-databases1.md)
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)
