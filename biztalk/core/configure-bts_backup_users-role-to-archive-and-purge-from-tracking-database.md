---
title: "How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "purging, BTS_BACKUP_USERS role"
  - "Tracking database, purging"
  - "BTS_BACKUP_USERS role"
  - "DTA Purge and Archive job"
  - "archiving [Tracking database], BTS_BACKUP_USERS role"
  - "archiving [Tracking database], DTA Purge and Archive job"
  - "Tracking database, BTS_BACKUP_USERS role"
  - "Tracking database, archiving"
  - "purging, DTA Purge and Archive job"
ms.assetid: c27aad2a-5788-4236-b5eb-ca730bf79851
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database
The DTA Purge and Archive (BizTAlkDTADb) job normally runs using the credentials of the logged-on SQL Server Agent service account user. For added security, however, you can configure the DTA Purge and Archive (BizTalkDTADb) job to run using the credentials of an account which is a member of the BTS_BACKUP_USERS role. This helps to prevent elevation of privileges by running SQL Server Agent jobs under accounts with essential permissions.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To configure the BTS_BACKUP_USERS role for archiving and purging data from the BizTalk Tracking database  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, specify the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL Server.  
  
3.  In **Microsoft SQL Server Management Studio**, double-click **BizTalkDTADb**, double-click **Security**, double-click **Roles**, and then double-click **Database Roles**.  
  
4.  In the **Object Explorer Details** pane, double-click **BTS_BACKUP_USERS**.  
  
5.  In the **Database Role Properties – BTS_BACKUP_USERS** dialog box, under **Members of this role**, click **Add**.  
  
6.  In the **Select Database User or Role** dialog box, enter a user account with SQL Server Agent Service credentials, and then click **OK**.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)