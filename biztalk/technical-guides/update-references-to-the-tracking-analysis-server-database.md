---
title: "Update References to the Tracking Analysis Server Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a403325-1394-4668-946f-01b610cb686e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update References to the Tracking Analysis Server Database
The Tracking Analysis Server database is an optional and contains the online analytical processing (OLAP) cubes. These OLAP cubes are aggregations of data contained in the BizTalk Tracking database.  
  
 To restore the Tracking Analysis Server database, use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager to process the MessageMetrics and ServiceMetrics cubes. For instructions, see [Managing Backing Up and Restoring (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (<http://go.microsoft.com/fwlink/?LinkId=130939>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.  
  
 To restore the Tracking Analysis Server database to an alternate computer, you must also update references to the database name in the BizTalk Management database by using the following procedure.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.  
  
### To update references to the Tracking Analysis Server database name  
  
1.  On the destination system, click **Start**, click **Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, select the **Server type** as **Database Engine**, provide a server name, provide the credentials to connect ot the server, and then click **Connect**.  
  
3.  Open the appropriate server by clicking it, double-clicking **Databases**, double-clicking **BizTalkMgmtDb**, and then clicking **Tables**.  
  
4.  In the details pane, right-click **adm_Group**, and then point to **Open Table**.  
  
5.  Modify the columns corresponding to the original database to reference the appropriate values for the new database.  
  
    > [!NOTE]  
    >  *\<DBType\>* DBServerName and *\<DBType\>* DBName indicate the location of the database, where *\<DBType\>* corresponds to the type of the database, for example, TrackingAnalysis.  
  
6.  Close the table to save the new values.  
  
## See Also  
 [Updating Database References](../technical-guides/updating-database-references.md)