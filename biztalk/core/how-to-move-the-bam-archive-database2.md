---
title: "How to Move the BAM Archive Database2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archive database [BAM], migrating"
  - "migrating, Archive database [BAM]"
ms.assetid: 88b96dc2-8c9c-43f5-afb9-a937e05de36b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Archive Database
You can use this procedure to move the BAM Archive database to another server.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To move the BAM Archive database  
  
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
  
2. Follow the instructions in SQL Server Books Online to back up the database on the old server.  
  
3. Copy the BAM Archive database to the new SQL server.  
  
4. Follow the instructions in SQL Server Books Online to restore the database on the new server.  
  
5. Edit the BAMConfiguration.xml file and change the ServerName in the ArchivingDatabase DeploymentUnit section to the new server name.  
  
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
  
## See Also  
 [Moving BizTalk Server Databases](../core/moving-biztalk-server-databases.md)