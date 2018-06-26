---
title: "Using BizTalk Server Log Shipping for Disaster Recovery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d65015c-de53-4590-b644-5c2f66f763db
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using BizTalk Server Log Shipping for Disaster Recovery
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implements database standby capabilities through the use of database log shipping. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping automates the backup and restore of database and transaction log files, allowing a standby server to resume database processing in the event that the production database server fails.  
  
## How Log Shipping Works  
 The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for log shipping synchronize data between the source server used in production and the destination server used as a standby every 15 minutes by default (every time that the Backup BizTalk Server job runs).  
  
## Using Log Shipping for Disaster Recovery  
 Do the following when using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping for disaster recovery:  
  
- Follow the steps in the topic [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) to increase availability of a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment using disaster recovery.  
  
- Verify that the disaster recovery servers have the capacity to handle production load.  
  
   Ensure that the standby servers have the same or similar resources available (CPU/memory/disk) as the production servers.  
  
- Ensure that the specifics of your disaster recovery routine are well documented.  
  
   Document every step of your disaster recovery preparation and implementation in detail. Disaster seldom strikes when it is convenient so assume that the parties responsible for implementing the disaster recovery procedure are starting their first day of work and will be doing this for the first time.  
  
- As part of regular testing, practice failover to the disaster recovery site, especially as new BizTalk applications are put in production.  
  
   Perform failover testing as a part of regular testing and maintenance to ensure that it can be performed smoothly.  
  
## See Also  
 [Disaster Recovery](../technical-guides/disaster-recovery.md)