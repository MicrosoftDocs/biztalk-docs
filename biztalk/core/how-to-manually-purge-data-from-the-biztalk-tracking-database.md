---
title: "How to Manually Purge Data from the BizTalk Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking database, purging"
  - "purging, manually"
  - "purging, warnings"
ms.assetid: f350d850-5034-4166-940c-8d10b7b445fb
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manually Purge Data from the BizTalk Tracking Database
The DTA Archive and Purge SQL Server Agent job reduces the need to manually purge data from the BizTalk Tracking (BizTalkDTADb) database due to continuous purging of the database and compaction of stored tracking data. You might need to manually purge data if your BizTalk Tracking (BizTalkDTADb) database has grown so much that sustained performance degradation is occurring and the DTA Archive and Purge job is unable to keep up with the database growth.  
  
> [!CAUTION]
>  Performing this procedure deletes all tracking data for completed instances from the BizTalk Tracking (BizTalkDTADb) database regardless of completion time. Before performing this procedure, you should archive the BizTalk Tracking (BizTalkDTADb) database separately from the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To manually purge data from the BizTalk Tracking database  
  
1. Backup your BizTalk Server databases.  
  
2. Archive the BizTalk Tracking (BizTalkDTADb) database.  
  
3. Open the Services console. Click **Start**, click **Run**, and then type **services.msc**. If a **User Account Control** dialog is displayed, click **Continue**.  
  
4. When the Services console appears, locate and then stop each of the following services. To stop a service, right-click the service row in the **Services** pane, and then click **Stop**.  
  
   -   BizTalkServiceBizTalkGroup : BizTalkServerApplication  
  
   -   Enterprise Single Sign-On Service  
  
        If the BizTalkServiceBizTalkGroup : BizTalkServerApplication service is running when you try to shut down the Enterprise Singe Sign-On Service, a **Stop Other Services** dialog will be displayed. Click **Yes**.  
  
   -   Rule Engine Update Service  
  
5. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**. If a **User Account Control** dialog is displayed, verify that the action described is what you want, and then click **Continue**.  
  
6. In the **BizTalk Server Administration Console** in the explorer pane on the left side of the window, double-click **BizTalk Group** to expand the list below it, then double-click **Platform Settings**, and then click **Host Instances**. This will display a list of host instances (the **Host Instances** pane) and related properties, on the right side of the screen.  
  
7. In the **Host Instances** pane, right-click each running host instance, and then click **Stop**.  
  
8. Click **Start**, go to **Run**, type **cmd**, and then click **OK**.  
  
9. At the command prompt, type:  
  
     **net stop iisadmin /y**  
  
     This stops the IIS Admin Service and all dependent services, one-by-one and prevents new data from being written to the BizTalkDTADb while data is being purged. Write down the list of services as each one is stopped. You will need to use this list of services later when you restart IIS.  
  
     Below is an example of the output you will see after issuing this command (the dependent services listed on your computer may vary):  
  
    ```  
    The following services are dependent on the IIS Admin Service service. Stopping the IIS Admin Service service will also stop these services.  
    World Wide Web Publishing Service  
    HTTP SSL  
    ```  
  
10. Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.  
  
11. In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL Server.  
  
12. In **Microsoft SQL Server Management Studio**, double-click **Databases**, double-click the **BizTalkDTADb** database, double-click **Programmability**, and then click **Stored Procedures**.  
  
13. In the **Object Explorer Details** pane, right-click **dtasp_PurgeAllCompletedTrackingData**, and then click **Execute Stored Procedure**.  
  
14. In the **Execute Procedure** dialog box, click **OK**.  
  
     This stored procedure deletes all tracking data associated with completed instances regardless of their completion time.  
  
15. Open Services. Click **Start**, click **Run**, and then type **services.msc**. If a **User Account Control** dialog is displayed, verify that the action described is what you want, and then click **Continue**.  
  
16. Right-click each of the following services, and then click **Start**:  
  
    -   BizTalkServiceBizTalkGroup : BizTalkServerApplication  
  
    -   Enterprise Single Sign-On Service  
  
    -   Rule Engine Update Service  
  
17. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
18. In the **BizTalk Server Administration Console**, double-click the **BizTalk Group**, double-click **Platform Settings**, and then click **Host Instances**.  
  
19. In the **Object Explorer Details** pane, right-click each stopped host instance, and then click **Start**.  
  
20. Start a command prompt, as described in step 8 above.  
  
21. At the command prompt, restart each of the IIS services that you stopped in step 4. Type:  
  
     **net start** *\<IISserviceName\>*  
  
     Where *\<IISserviceName\>* is the name of the IIS service you want to restart. You must repeat this command for each of the IIS services.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)   
 [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)