---
title: "How to Move the BAM Primary Import Database2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc4f2656-2faa-4503-9551-05e1b6eceb1a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Primary Import Database
You can use this procedure to move the BAM Primary Import database to another server. From an end-to-end scenario perspective, moving the BAM Primary Import database involves two major steps:  
  
-   [Moving the BAM Primary Import Database](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_MovingBAMPI)  
  
-   [Updating References to the New BAM Primary Import Database](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)  
  
## Prerequisites  
 You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.  
  
##  <a name="BKMK_MovingBAMPI"></a> Moving the BAM Primary Import Database  
 Perform the steps in the following procedure to move the BAM Primary Import database.  
  
#### To move the BAM Primary Import database  
  
1. Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Primary Import database.  
  
2. Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
3. Stop the IIS service.  
  
4. Stop the BAM Alerts Notification service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
        **Net stop NS$BamAlerts**  
  
5. Back up the BAM Primary import database on the old server. For instructions on backing up a database, follow the instructions on how to back up a database at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.  
  
6. Copy the BAM Primary Import database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.  
  
7. Restore the BAM Primary import database on the new server. For instructions on restoring the database, follow the instructions on how to restore a database at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.  
  
   > [!NOTE]  
   >  If you restore the BAM Primary Import database from a backup, then you should also restore the BAM Archive, BAM Star Schema, and BAM Analysis databases by using a backup older than the BAM Primary backup.  
  
##  <a name="BKMK_BAMPIRef"></a> Updating References to the New BAM Primary Import Database  
 After you have moved the database, you must update all the references to the new BAM Primary Import Database. The following references must be updated:  
  
-   Update all the BizTalk databases with the new server name. You can do so by using the UpdateDatabase.vbs script. See [To update BizTalk Databases with the new server name](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB).  
  
-   Update the Web.config file for the BAM portal. See [To update the Web.config file for the BAM portal](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config).  
  
-   Update the reference to the BAM Primary Import Database in all BAM Livedata Microsoft Excel files. See [To update reference in BAM Livedata Microsoft Excel files](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel).  
  
-   Update the new server and database names in all BAM analysis SSIS packages. See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg).  
  
-   Update the new server and database names in data sources for all OLAP cubes. See [To update server and database names in data sources for all OLAP cubes](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP).  
  
###  <a name="BKMK_UpdateDB"></a> To update BizTalk Databases with the new server name  
  
1. On a computer running BizTalk Server, browse to the following folder:  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\bins32\Schema\Restore**  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
2. Right-click **SampleUpdateInfo.xml**, and then click **Edit**.  
  
3. Comment out all of the database sections except for the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.  
  
4. In the `OldPrimaryImportDatabase` section of the file, for the `ServerName` property, replace **SourceServer** with the name of existing server where the database resides.  
  
5. In the `PrimaryImportDatabase` section of the file, for the `ServerName` property, replace **DestinationServer** with the name of the server where you have moved the BAM Primary Import database  
  
6. For the BizTalkMgmtDb, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the "SourceServer" and "Destination Server" to the name of the existing server where those databases reside.  
  
   > [!IMPORTANT]
   >  Include the quotation marks around the name of the source and destination systems.  
   > 
   > [!NOTE]
   >  If you renamed any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must also update the database names as appropriate.  
  
7. When you are finished editing the file, save it and exit.  
  
8. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
9. At the command prompt, navigate to the following directory:  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
10. At the command prompt, type:  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
###  <a name="BKMK_Config"></a> To update the Web.config file for the BAM portal  
  
1.  On a computer running BizTalk Server, update the Web.config files under **\<drive\>:\Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**. Update the server and database names in the following section in the Web.config:  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
    </appSettings>  
    ```  
  
2.  On a computer running BizTalk Server, update the Web.config files under **\<drive\>:\Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**. Update the server and database names in the following section in the Web.config:  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
      <add key="MaxResultRows" value="2000" />  
    </appSettings>  
    ```  
  
3.  Save and close the files.  
  
###  <a name="BKMK_UpdateExcel"></a> To update reference in BAM Livedata Microsoft Excel files  
  
1. Open the Excel live data file. The file name ends with _LiveData.xls.  
  
2. On the **BAM** menu, click **BAM DB Connection**.  
  
3. In the **Select BAM Database** dialog box, enter the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer and the BAMPrimaryImport database, and then click **OK**.  
  
4. On the **File** menu, click **Close and Return to Microsoft Excel**.  
  
5. On the **File** menu, click **Save**.  
  
###  <a name="BKMK_UpdatePckg"></a> To update server and database names in all BAM SSIS packages  
  
1.  Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_" or "BAM_DM_". To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.  
  
2.  In SQL Server Business Intelligence Development Studio, create a new project. Click **File**, click **New**, and then click **Project**.  
  
3.  In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**. In the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.  
  
4.  In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.  
  
5.  In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_* and BAM_DM_* packages.  
  
6.  In **Package Path**, click the ellipses button.  
  
7.  In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.  
  
     The package is now listed in Solution Explorer.  
  
8.  In Solution Explorer, double-click the package you added in the previous step. In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 1 (BAMPrimaryImport database).  
  
9. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.  
  
10. Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **PrimaryImportDatabase** and **PrimaryImportServer** variables. You must update the values to point to the new server and database.  
  
    > [!NOTE]  
    >  Repeat step 4 through 10 for all the packages that you want to update.  
  
11. Click then **File** menu, and then click **Save All**.  
  
12. Start the SQL Server Management Studio. Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.  
  
13. In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.  
  
14. Specify the server name and credentials to connect to the server and click **OK**.  
  
15. In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.  
  
16. In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.  
  
17. In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.  
  
18. In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.  
  
19. Click inside the Package Name box to automatically populate the box.  
  
    > [!NOTE]  
    >  Repeat step 16 through 19 for all the packages that you want to update.  
  
20. Click **OK**, and then click **Yes** to overwrite.  
  
21. Enable any BAM cube update and data maintenance SSIS packages.  
  
###  <a name="BKMK_UpdateDSOLAP"></a> To update server and database names in data sources for all OLAP cubes  
  
1. Update the server and database names in data sources for all OLAP cubes. To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.  
  
2. In the **Connect to Server** dialog box, for the **Server type** drop-down list select **Analysis Services**, provide the server name, select an authentication method (and provide credentials if required), and then click **Connect**.  
  
3. In the Object Explorer, expand **Databases**, expand **BAMAnalysis**, expand **Data Sources**, and then double-click a data source.  
  
4. In the **Data Source Properties** dialog box, click the ellipsis button **(…)** against the **Connection String** property.  
  
5. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server hosting the BAMPrimaryImport database, click **OK**, and then click **OK**.  
  
6. Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
7. Start the IIS service.  
  
8. Start the BAM Alerts Notification service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
        **Net start NS$BamAlerts**  
  
9. Resolve any incomplete trace instances.  For information about resolving incomplete BAM activity instances, see [How to Resolve Incomplete Activity Instances](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).  
  
## See Also  
 [Moving Databases](../technical-guides/moving-databases.md)