---
title: "How to Manually Purge Data from the MessageBox Database in a Test Environment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 398991a9-344a-487a-a817-dfc97d48ebe6
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manually Purge Data from the MessageBox Database in a Test Environment
When running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a development or test environment, data that is stored in the MessageBox database is not usually business critical "live" data and therefore may be deleted. In these scenarios, you may need a "quick and dirty" method for purging data from the MessageBox database. Follow the procedures in this topic to manually purge data from the MessageBox database using the bts_CleanupMsgbox stored procedure.  
  
> [!NOTE]
>  You should only perform these steps in a test environment. Manually purging the BizTalk MessageBox database in a production environment is not supported.  
  
### To stop BizTalk services  
  
1.  Stop any instances of the BizTalk service from the Services console.  
  
2.  If you are running any adapters in isolated hosts (for example HTTP, SOAP, or WCF), restart IIS by running the IISRESET from a command prompt.  
  
3.  Shut down any custom Isolated Adapters that are running.  
  
### To create and execute the bts_CleanupMsgbox stored procedure using SQL Server 2008  
  
1. Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2. In the **Connect to SQL Server** dialog box, select the SQL server and the appropriate authentication method, and then click **Connect**.  
  
3. In the **Available databases** drop-down list, select the BizTalk Messagebox database (**BizTalkMsgBoxDB** by default).  
  
4. Click the **New Query** icon on the toolbar.  
  
5. Open the **msgbox_cleanup_logic.sql** file from SQL Server Management Studio. The msgbox_cleanup_logic.sql file is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\ directory of the BizTalk Server computer.  
  
6. Click the **Execute Query** icon on the toolbar to run the script to create the bts_CleanupMsgbox stored procedure. The bts_CleanupMsgbox stored procedure can then be viewed in the list of stored procedures as dbo.bts_CleanupMsgbox.  
  
7. Click the **New Query** icon on the toolbar.  
  
8. Paste the following command into the new query window:  
  
   ```  
   exec bts_CleanupMsgbox  
   ```  
  
9. Click the **Execute Query** icon on the toolbar to run the bts_CleanupMsgbox stored procedure.  
  
   > [!IMPORTANT]
   >  Do not run the bts_CleanupMsgbox stored procedure on a production server that is running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You should only run the bts_CleanupMsgbox stored procedure in a test environment. Running the bts_CleanupMsgbox stored procedure in a production environment is not supported.  
  
10. Restart BizTalk services as needed.  
  
## Considerations when running the bts_CleanupMsgbox stored procedure  
 The following considerations apply when running the bts_CleanupMsgbox stored procedure:  
  
1.  If you install a hot fix onto your test system that updates the BizTalk database schemas, the hot fix may overwrite the bts_CleanupMsgbox stored procedure with an empty version of this stored procedure. In this case, you will need to follow the procedures outlined in this topic to recreate the bts_CleanupMsgbox stored procedure.  
  
2.  If you create a new MessageBox database, the bts_CleanupMsgbox stored procedure will be empty and you will need to follow the procedures outlined in this topic to recreate the bts_CleanupMsgbox stored procedure.  
  
3.  Use of the bts_CleanupMsgbox stored procedure is **not supported** on a production system. This stored procedure will delete all of the data in your MessageBox database.  
  
## See Also  
 [How to Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)