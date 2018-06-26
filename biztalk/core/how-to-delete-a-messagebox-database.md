---
title: "How to Delete a MessageBox Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, MessageBox database"
  - "managing [MessageBox database], deleting"
  - "MessageBox database, deleting"
ms.assetid: 51f91fcb-8b97-4b00-9056-6d216c8ccb58
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete a MessageBox Database
You use the BizTalk Administration Console or Windows Management Instrumentation (WMI) to remove a MessageBox database from a BizTalk group. You can remove a MessageBox database from a BizTalk group, or you can delete it from your BizTalk Server deployment entirely.  
  
 For example, you can delete a MessageBox database you are no longer using, such as a database used for testing purposes.  
  
 There are eight steps to permanently and completely removing MessageBox databases from your BizTalk Server deployment:  
  
1.  Disable new message publication.  
  
     You must disable the publication of new messages before you delete a MessageBox database. For information about disabling new message publication, see [How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md).  
  
2.  Wait for the cache refresh interval to expire.  
  
     After you disable the publication of new messages, you must wait before you delete the database. The wait time is defined as twice the length of the CacheRefreshInterval. The default value of CacheRefreshInterval is 60 seconds. You use the **Group Properties** dialog box to change the Cache Refresh.  
  
3.  Remove the MessageBox database from the BizTalk Group.  
  
     Removing the MessageBox database from the BizTalk Group removes the MessageBox reference from the BizTalk Management database.  
  
4.  Restart host instances that contain cached connections to the MessageBox database.  
  
     You must restart the host instance before physically deleting the database from SQL Server if cached database connections from the run-time engine are present. For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).  
  
5.  Stop all in-progress host instances that access the database. For information about stopping an in-progress host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).  
  
     If you are removing a non-primary MessageBox database, before stopping an in-progress host instance, you should first disable publication of new messages to that message box and make sure that:  
  
    -   There are no running service instances remaining in the message box.  
  
    -   There are no suspended (or any other remaining) instances left in the message box.  
  
    -   BAM tracked data has been moved to the BizTalk Tracking (BizTalkDTADb) database (TrackingData table should be empty).  
  
    -   Tracked message bodies have been moved to the BizTalk Tracking (BizTalkDTADb) database.  
  
6.  Ensure that the background SQL Server Agent job is finished.  
  
     Before you permanently delete a MessageBox database from your BizTalk Server deployment, you should first ensure that the background SQL Server Agent job has finished transferring all tracked message bodies to the TrackingSpool table, and then back up the TrackingSpool tables. For information about checking the status of a background SQL Server Agent job, see SQL Server Books Online.  
  
7.  Back up the TrackingSpool tables.  
  
     Tracked message bodies remain in the MessageBox database until you manually back up the TrackingSpool tables into external storage. Before the backup happens, a background SQL Server Agent job transfers the message bodies from the Spool table to the TrackingSpool table. For information about manually backing up SQL Server tables, see SQL Server Books Online.  
  
8.  Remove the database from SQL Server.  
  
     Deleting a MessageBox database from a BizTalk Group does not physically remove the database from Microsoft SQL Server. To permanently delete the MessageBox database, you must remove it by using SQL Server Enterprise Manager or SQL Server Management Studio after it is removed from the BizTalk Group.  
  
## Prerequisites  
 Administrators who manage MessageBox databases must have the required user rights. You must have the following user rights to manage MessageBox databases and disable new message publication:  
  
-   You must be logged on as a member of the BizTalk Server Administrators group.  
  
-   You must be a SQL Server Administrator on the computer where the database exists.  
  
### To delete a MessageBox database from a BizTalk Group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Message Boxes**.  
  
3. In the details pane, right-click the message box database you want to remove, and then click **Properties**.  
  
4. In the **Message Box Properties** dialog box, select the **Disable new message publication** check box.  
  
5. Use the Group Hub page in the BizTalk Server Administration Console to verify that no message instances are dehydrated or suspended on the MessageBox database you are deleting.  
  
6. Wait for a period of time twice the length of the CacheRefreshInterval. The default value of CacheRefreshInterval is 60 seconds.  
  
7. In the details pane, right-click the MessageBox database that you want to delete, and click **Delete**.  
  
8. After reading the warning message, click **OK**.  
  
9. In the console tree, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.  
  
10. In the details pane, right-click all running host instances, and stop and restart each one.  
  
11. On the server where the MessageBox database resides, open SQL Server Enterprise Manager or SQL Server Management Studio, depending on which version of SQL Server you are using, and then delete the database.  
  
     For information about how to delete a database in SQL Server, see SQL Server Books Online.  
  
## See Also  
 [Managing MessageBox Databases](../core/managing-messagebox-databases.md)   
 [How to Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md)   
 [How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md)   
 [The MessageBox Database](../core/the-messagebox-database.md)