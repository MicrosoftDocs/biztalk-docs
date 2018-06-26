---
title: "How to Move the BAM Star Schema Database2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6832ac2-c8c5-4515-883e-26d125d6ace0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Star Schema Database
You can use this procedure to move the BAM Star Schema database to another server.  From an end-to-end scenario perspective, moving the BAM Star Schema database involves two major steps:  
  
-   [Moving the BAM Star Schema Database](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarMoveDB)  
  
-   [Updating References to the New BAM Star Schema Database](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate)  
  
## Prerequisites  
 You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.  
  
##  <a name="BKMK_StarMoveDB"></a> Moving the BAM Star Schema Database  
 Perform the steps in the following procedure to move the BAM Star Schema database.  
  
#### To move the BAM Star Schema database  
  
1. Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Star Schema database.  
  
2. Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
3. Stop the IIS service.  
  
4. Stop the BAM Alerts Notification service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
        **Net stop NS$BamAlerts**  
  
5. Back up the BAM Star Schema database on the old server. For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.  
  
6. Copy the BAM Star Schema database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.  
  
7. Restore the BAM Star Schema database on the new server. For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.  
  
##  <a name="BKMK_StarUpdate"></a> Updating References to the New BAM Star Schema Database  
 After you have moved the database, you must update all the references to the new BAM Star Schema Database. The following references must be updated:  
  
-   Update the BAM configuration with the new database and server names. See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateBAMConfig).  
  
-   Update the new server and database names in all BAM analysis SSIS packages. See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateRef).  
  
-   Update the new server and database names in data sources for all non-OLAP cubes. See [To update server and database names in data sources for all non-OLAP cubes](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_UpdateDS_non_OLAP).  
  
###  <a name="BKMK_StarUpdateBAMConfig"></a> To update the BAM configuration  
  
1. Get a copy of the .xml file used for restoring BAM:  
  
   1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2. On a computer running BizTalk Server, browse to the following folder:  
  
      - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:  
  
         **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**  
  
      - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
   3. At the command prompt, type:  
  
       **Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername\> -database:\<database\>**  
  
      > [!NOTE]
      >  When running this command, substitute the actual name of the server from which to get the configuration information for \<servername\> and substitute the actual name of the database from which to get the configuration information for \<database\>. For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (<http://go.microsoft.com/fwlink/?LinkId=156516>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
2. Edit the BAMConfiguration.xml file and change the **ServerName** in the `<DeploymentUnit Name="StarSchemaDatabase">` section to the new server name.  
  
3. Save and close the BAMConfiguration.xml file.  
  
4. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
5. On a computer running BizTalk Server, browse to the following folder:  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
6. At the command prompt, type:  
  
    **bm.exe update-config -FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_StarUpdateRef"></a> To update server and database names in all BAM SSIS packages  
  
1.  Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_". To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.  
  
2.  In SQL Server Business Intelligence Development Studio, create a new project. Click **File**, click **New**, and then click **Project**.  
  
3.  In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**. On the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.  
  
4.  In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.  
  
5.  In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_* packages.  
  
6.  In **Package Path**, click the ellipses button.  
  
7.  In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.  
  
     The package is now listed in Solution Explorer.  
  
8.  In Solution Explorer, double-click the package you added in the previous step. In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 2 (BAMStarSchema database).  
  
9. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.  
  
    > [!NOTE]  
    >  Repeat this for data source number 3 (MSDB database).  
  
10. In the **Connection Managers** tab, double-click data source number 4 (BAMAnalysis database). In the **Add Analysis Services Connection Manager** dialog box, click **Edit**.  
  
11. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, click **OK**, and then click **OK**.  
  
12. Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **AnalysisDatabase**, **AnalysisServer**, **PrimaryImportDatabase**, **PrimaryImportServer**, **StarSchemaDatabase**, and **StarSchemaServer** variables. You must update the values to point to the new server and database.  
  
    > [!NOTE]  
    >  Repeat step 4 through 12 for all the packages that you want to update.  
  
13. Click then **File** menu, and then click **Save All**.  
  
14. Start the SQL Server Management Studio. Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.  
  
15. In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.  
  
16. Specify the server name and credentials to connect to the server and click **OK**.  
  
17. In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.  
  
18. In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.  
  
19. In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.  
  
20. In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.  
  
21. Click inside the Package Name box to automatically populate the box.  
  
    > [!NOTE]  
    >  Repeat step 18 through 21 for all the packages that you want to update.  
  
22. Click **OK**, and then click **Yes** to overwrite.  
  
23. Enable any BAM cube update and data maintenance SSIS packages.  
  
###  <a name="BKMK_UpdateDS_non_OLAP"></a> To update server and database names in data sources for all non-OLAP cubes  
  
1. Update the server and database names in data sources for all non-OLAP cubes. To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.  
  
2. In the **Connect to Server** dialog box, for the **Server type** drop-down list select **Analysis Services**, provide the server name, select an authentication method (and provide credentials if required), and then click **Connect**.  
  
3. In the Object Explorer, expand **Databases**, expand **BAMAnalysis**, expand **Data Sources**, and then double-click a data source.  
  
4. In the **Data Source Properties** dialog box, click the ellipsis button **(…)** against the **Connection String** property.  
  
5. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server hosting the BAMStarSchema database, click **OK**, and then click **OK**.  
  
6. Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
7. Start the IIS service.  
  
8. Start the BAM Alerts Notification service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
        **Net start NS$BamAlerts**  
  
9. Resolve any incomplete trace instances.  For information about resolving incomplete BAM activity instances, see [How to Resolve Incomplete Activity Instances](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).  
  
> [!TIP]  
>  As a good practice, you should also move the BAM_AN_* SSIS packages to the server hosting the BAMStarSchema database.  
  
## See Also  
 [Moving Databases](../technical-guides/moving-databases.md)