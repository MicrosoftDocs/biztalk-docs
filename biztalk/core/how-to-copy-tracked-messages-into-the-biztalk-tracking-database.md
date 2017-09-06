---
title: "How to Copy Tracked Messages into the BizTalk Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, copying between servers"
  - "MessageBox database, Tracking database"
  - "Tracking database, linking servers"
  - "MessageBox database, copying messages"
  - "linking, servers"
  - "Tracking database, archiving"
  - "archiving [Tracking database], linking servers"
  - "Tracking database, MessageBox database"
  - "Tracking database, copying messages"
  - "archiving [Tracking database], MessageBox database"
  - "MessageBox database, linking servers"
  - "MessageBox database, archiving"
ms.assetid: 369e972a-efbe-4ad5-a68f-aa3bbfb9ad54
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Copy Tracked Messages into the BizTalk Tracking Database
The archiving and purging process potentially accesses and/or updates databases in different SQL servers, so you must set up linked servers between the involved SQL Server instances. You can directly copy tracked messages from the BizTalk MessageBox (BizTalkMsgBoxDb) database server to your BizTalk Tracking (BizTalkDTADb) database using a linked server. You must set up linked servers between:  
  
-   Each of your BizTalk MessageBox (BizTalkMsgBoxDb) databases and the BizTalk Tracking (BizTalkDTADb) database.  
  
-   The BizTalk Tracking (BizTalkDTADb) database and the validating server for archive validation.  
  
-   The service accounts for the SQL Server Agent on the computer hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database must have the db_datareader and db_datawriter permissions for the BizTalk Tracking (BizTalkDTADb) database on the linked server.  
  
> [!NOTE]
>  In SQL Server Agent, verify that the copy job runs without errors. Otherwise, errors might prevent data from being moved to the tracking database.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To copy tracked messages into the BizTalk Tracking database (SQL Server 2008)  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, specify the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL server.  
  
3.  In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.  
  
4.  In the details pane, right-click **TrackedMessages_Copy_BizTalkMsgBoxDb**, and then click **Properties**.  
  
5.  In the **Job Properties - TrackedMessages_Copy_BizTalkMsgBoxDb** dialog box, under **Select a page**, click **Steps**.  
  
6.  Under **Job step list**, click **Purge**, and then click **Edit**.  
  
7.  In the **Command** box, edit the tracking server and database names parameters as appropriate, and then click **OK**.  
  
8.  On the **Job Properties - TrackedMessages_Copy_BizTalkMsgBoxDb** dialog box, under **Select a page**, click **General**,select the **Enabled** check box, and then click **OK**.  
  
     The messages will be copied from the BizTalk MessageBox (BizTalkMsgBoxDb) to the BizTalk Tracking (BizTalkDTADb) database.  
  
> [!IMPORTANT]
>  If you add a new MessageBox database, you will need to perform this procedure again for the new MessageBox database.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)