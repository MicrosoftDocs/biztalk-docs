---
title: "How to Move the BAM Notification Services Databases2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Notification Services Application database [BAM]"
  - "Notification Services Instance database [BAM]"
  - "migrating, Notification Services database [BAM]"
ms.assetid: 4b7f3397-65c9-4c71-8374-8764f4c2e2e3
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Notification Services Databases
You can use this procedure to move the BAM Notification Services databases to another server.  
  
> [!NOTE]
>  You must move the BAM Notification Services Application (BAMAlertsApplication) database and BAM Notification Services Instance (BAMAlertsNSMain) database together.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To move the BAM Notification Services databases  
  
1. Get a copy of the .xml file used for restoring BAM:  
  
   1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2. At the command prompt, navigate to the following directory:  
  
       **%SystemDrive%\Program Files\Microsoft**  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**  
  
   3. At the command prompt, type:  
  
      ```  
      Bm.exe get-config –filename:BAMConfiguration.xml  
      ```  
  
      > [!NOTE]
      >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
2. At the command prompt, type:  
  
   ```  
   Net stop NS$BamAlerts  
   ```  
  
3. Follow the instructions in SQL Server Books Online on how to back up the database on the old server.  
  
4. Copy the BAM Notification Services databases to the new SQL server.  
  
5. Follow the instructions in SQL Server Books Online on how to restore the database on the new server.  
  
6. Edit the BAMConfiguration.xml file and change the ServerName in the Alert DeploymentUnit section to the new server name.  
  
7. Save and close the BAMConfiguration.xml file.  
  
8. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
9. At the command prompt, navigate to the following directory:  
  
     **%SystemDrive%\Program Files\Microsoft**  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**  
  
10. At the command prompt, type:  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
11. Update references to the BAM Notification Services databases. For more information, see [How to Update References to the BAM Notification Services Databases](../core/how-to-update-references-to-the-bam-notification-services-databases.md).  
  
## See Also  
 [Moving BizTalk Server Databases](../core/moving-biztalk-server-databases.md)