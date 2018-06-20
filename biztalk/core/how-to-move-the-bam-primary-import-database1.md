---
title: "How to Move the BAM Primary Import Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migrating, Primary Import database [BAM]"
  - "Primary Import database [BAM], migrating"
ms.assetid: fab13fea-5c35-4a9f-977d-cc45545c54b2
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Primary Import Database
You can use this procedure to move the BAM Primary Import database to another server.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To move the BAM Primary Import database  
  
1. Stop all BizTalk Server services. For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
2. Stop the IIS service.  
  
3. Stop the BAM Alerts Notification Service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
       ```  
       Net stop NS$BamAlerts  
       ```  
  
4. Follow the instructions in SQL Server Books Online to back up the BAM Primary Import database on the old server.  
  
5. Copy the BAM Primary Import database to the new SQL Server.  
  
6. Follow the instructions in SQL Server Books Online to restore the BAM Primary Import database on the new server.  
  
7. On a computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], browse to the following folder:  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore  
  
8. Right-click **SampleUpdateInfo.xml**, and then click **Edit**.  
  
9. In the Primary Import Database section of the file, replace **"SourceServer"** with the name of the source system, and then replace **"DestinationServer"** with the name of the destination system.  
  
    > [!IMPORTANT]
    >  Include the quotation marks around the name of the source and destination systems.  
  
    > [!NOTE]
    >  If you renamed any of the BizTalk Server databases, you must also update the database names as appropriate.  
  
10. Uncomment the following lines in the xml file:  
  
    ```  
    - <UpdateConfiguration>  
      <MessageBoxDB oldDBName="BizTalkMsgboxDb" oldDBServer="Server01" newDBName="BizTalkMsgboxDb" newDBServer="Server01" IsMaster="1" />   
      <TrackingDB oldDBName="BizTalkDTADb" oldDBServer="Server01" newDBName="BizTalkDTADb" newDBServer="Server01" />   
      <ManagementDB oldDBName="BizTalkMgmtDb" oldDBServer="Server01" newDBName="BizTalkMgmtDb" newDBServer="Server01" />   
    - <BAM>  
    - <DeploymentUnit Name="OldPrimaryImportDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="PrimaryImportDatabase">  
      <Property Name="ServerName">Server02</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="ArchivingDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMArchive</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="AnalysisDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMAnalysis</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="StarSchemaDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMStarSchema</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="Alert">  
      <Property Name="DBServer">Server01</Property>   
      <Property Name="InstanceDatabaseName">BAMAlerts</Property>   
      </DeploymentUnit>  
      </BAM>  
    - <OtherDatabases>  
      <Database Name="SSO" oldDBName="SSODB" oldDBServer="Server01" newDBName="SSODB" newDBServer="Server01" />   
      </OtherDatabases>  
      </UpdateConfiguration>  
    ```  
  
11. When you are finished editing the file, save it and exit.  
  
12. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
13. At the command prompt, navigate to the following directory:  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore  
  
14. At the command prompt, type:  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
15. Update the reference to BAM Primary Import Database in all BAM Livedata Microsoft Excel files. For each file:  
  
    1.  Open the Excel live data file. The file name ends with _LiveData.xls.  
  
    2.  On the **BAM** menu, click **BAM DB Connection**.  
  
    3.  In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.  
  
    4.  On the **File** menu, click **Close and Return to Microsoft Excel**.  
  
    5.  On the **File** menu, click **Save**.  
  
16. Update the server and database names in all BAM analysis DTS packages, which are prefixed with "BAM_AN_" or "BAM_DM_" by following these steps:  
  
    1.  On the server hosting BAM, open SQL Server Enterprise Manager.  
  
    2.  Open the **Data Transformation Services** folder.  
  
    3.  Open the **Local Packages** folder, and then open the DTS packages.  
  
    4.  On the **Package** menu, click **Properties**.  
  
    5.  On the **Global Variables** tab, update the values for the primary import server and database.  
  
    6.  Change the following lines to match your new server and database:  
  
         PrimaryImportServer= "*\<ServerName\>*"  
  
         PrimaryImportDatabase = "*\<DatabaseName\>*"  
  
17. Start all BizTalk Server services. For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
18. Start the IIS service.  
  
19. Start the BAM Alerts Notification Service:  
  
    1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
    2.  At the command prompt, type:  
  
        ```  
        Net start NS$BamAlerts  
        ```  
  
## See Also  
 [Moving BizTalk Server Databases](../core/moving-biztalk-server-databases.md)