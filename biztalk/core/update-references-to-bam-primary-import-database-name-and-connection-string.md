---
title: "How to Update References to the BAM Primary Import Database Name and Connection String | Microsoft Docs"
ms.custom: ""
ms.date: "02/01/2018"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Update References to the BAM Primary Import Database Name and Connection String
If you backed up your BAMPrimaryImport database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.  
  
 The BAM Event Bus service moves event data from the MessageBox database to the BAMPrimaryImport database. The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data. For more information about the BAM Event Bus service, see [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md).  
  
 To restore the BAMPrimaryImport database, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md). In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:  
  
-   Update the SQL Connection 1 in all BAM DTS packages to refer to the new database name.  
  
-   Update the web.config file with the new database name.  
  
-   Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.  
  
### To update references to the BAMPrimaryImport database name and connection string  
  
1.  Stop any BAM cube update and data maintenance Data Transformation Services (DTS) packages, or prevent them from running until you have restored the BAMPrimaryImport database.  
  
2.  Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.  
  
    1.  Click **Start**, click **Run**, and then type **services.msc**.  
  
    2.  Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.  
  
3.  Restore the BAMPrimaryImport database, performing the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).  
  
4.  Update the following Web.Config files:  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BamManagementService\Web.Config.  
  
         Replace the *\<ServerName\>* string with the new server name and *\<DatabaseName\>* with the new database name. Update the following connection strings:  
  
         \<appSettings\>  
  
         <add key="BamServer" value="*\<ServerName\>*" /\>  
  
         <add key="BamDatabase" value="*\<DatabaseName\>*" /\>  
  
         \<add key="MaxResultRows" value="2000" /\>  
  
         \</appSettings\>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BamQueryService\Web.Config.  
  
         Replace the *\<ServerName\>* string with the new server name and *\<DatabaseName\>* with the new database name. Update the following connection strings:  
  
         \<appSettings\>  
  
         \<add key="BamServer" value="*\<ServerName\>*" /\>  
  
         \<add key="BamDatabase" value="*\<DatabaseName\>*" /\>  
  
         \<add key="MaxResultRows" value="2000" /\>  
  
         \</appSettings\>  
  
5.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
6.  Navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.  
  
7.  Right-click **SampleUpdateInfo.xml**, and then click **Edit**.  

  
    1.  Comment out all of the database sections except for the  OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert. 
    2.  For the OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the **SourceServer** and **Destination Server** to the name of the existing server where those databases reside.  
  
    3.  For PrimaryImportDatabase, set the **"SourceServer"** to the name of the server where you have moved the BAM Primary Import database.  
  
        > [!IMPORTANT]
        >  Include the quotation marks around the name of the source and destination systems.  
  
        > [!NOTE]
        >  If you renamed any of the BizTalk Server databases, you must also update the database names as appropriate.  
  
    4.  When you are finished editing the file, save it and exit.  
  
8.  At the command prompt, type:  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
    > [!NOTE]
    >  You only need to run UpdateDatabase.vbs once.  
  
    > [!NOTE]
    >  On 64-bit computers, you must run UpdateDatabase.vbs from a 64-bit command prompt.  
  
9. At the command prompt, navigate to the following directory:  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
10. At the command prompt, edit bm.exe.config, change the value of key="DefaultServer" to the new server name, and then save the file.  
  
11. Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files. For each file:  
  
    1.  Open the Excel live data file. The file name ends with _LiveData.xls.  
  
    2.  On the **BAM** menu, click **BAM DB Connection**.  
  
    3.  In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.  
  
    4.  On the **File** menu, click **Close and Return to Microsoft Excel**.  
  
    5.  On the **File** menu, click **Save**.  
  
12. Restart the BizTalk Application service.  
  
    1.  Click **Start**, click **Run**, and then type **services.msc**.  
  
    2.  Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.  
  
13. Enable any BAM cube update and data maintenance DTS packages.  
  
14. To resolve any incomplete trace instances, see [How to Resolve Incomplete Activity Instances](../core/how-to-resolve-incomplete-activity-instances.md).  
  
## See Also  
 [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)
