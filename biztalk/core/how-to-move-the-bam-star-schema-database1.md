---
title: "How to Move the BAM Star Schema Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Star Schema database [BAM], migrating"
  - "migrating, Star Schema database [BAM]"
ms.assetid: b4a5f8fc-0dc4-4987-b96f-ecd49bd4dba3
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Star Schema Database
You can use this procedure to move the BAM Star Schema database to another server.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To move the BAM Star Schema database  
  
1. Get a copy of the .xml file used for restoring BAM:  
  
   1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2. At the command prompt, navigate to the following directory:  
  
       [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
   3. At the command prompt, type:  
  
      ```  
      Bm.exe get-config –filename:BAMConfiguration.xml  
      ```  
  
      > [!NOTE]
      >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
2. Follow the instructions in SQL Server Books Online on how to back up the database on the old server.  
  
3. Copy the BAM Star Schema database to the new SQL Server.  
  
4. Follow the instructions in SQL Server Books Online on how to restore the database on the new server.  
  
5. Edit the BAMConfiguration.xml file and change the ServerName in the StarSchemaDatabase DeploymentUnit section to the new server name.  
  
6. Save and close the BAMConfiguration.xml file.  
  
7. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
8. At the command prompt, navigate to the following directory:  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
9. At the command prompt, type:  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
10. Update SQL Connection 2 to change the server and database name in all BAM analysis DTS packages, which are prefixed with "BAM_AN_", by following these steps:  
  
    1.  Using SQL Server Management Studio, open the server hosting BAM.  
  
    2.  Open the **Data Transformation Services** folder.  
  
    3.  Open the **Local Packages** folder.  
  
    4.  Open the DTS package, and then double-click **Connection 2** to open the connection.  
  
    5.  Select the new server and database name in the drop-down box.  
  
11. Update the data source in the BAM Analysis database as follows:  
  
    1.  Using SQL Server Analysis Manager, open the server hosting the BAM Analysis database.  
  
    2.  Open the **Data Sources** folder.  
  
    3.  Right-click the data source for the cube, and then click **Edit**.  
  
    4.  On the **Connection** tab, type the new server name and database name for the BAM Star Schema database, and then click **OK**.  
  
## See Also  
 [Moving BizTalk Server Databases](../core/moving-biztalk-server-databases.md)