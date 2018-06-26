---
title: "How to Move the BAM Archive Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e371321c-6b8d-4be6-a6d2-926f6218db01
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Archive Database
You can use this procedure to move the BAM Archive database to another server.  From an end-to-end scenario perspective, moving the BAM Archive database involves two major steps:  
  
-   [Moving the BAM Archive Database](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_MovingArch)  
  
-   [Updating References to the New BAM Archive Database](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)  
  
## Prerequisites  
 You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.  
  
##  <a name="BKMK_MovingArch"></a> Moving the BAM Archive Database  
 Perform the steps in the following procedure to move the BAM Archive database.  
  
#### To move the BAM Archive database  
  
1. Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Archive database.  
  
2. Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
3. Stop the IIS service.  
  
4. Stop the BAM Alerts Notification service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
        **Net stop NS$BamAlerts**  
  
5. Back up the BAM Archive database on the old server. For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.  
  
6. Copy the BAM Archive database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.  
  
7. Restore the BAM Archive database on the new server. For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.  
  
##  <a name="BKMK_UpdateArch"></a> Updating References to the New BAM Archive Database  
 After you have moved the database, you must update all the references to the new BAM Archive Database. The following references must be updated:  
  
-   Update the BAM configuration with the new database and server names. See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchConfig).  
  
-   Update the new server and database names in all BAM analysis SSIS packages. See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchSSIS).  
  
###  <a name="BKMK_UpdateArchConfig"></a> To update the BAM configuration  
  
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
  
2. Edit the BAMConfiguration.xml file and change the **ServerName** in the `<DeploymentUnit Name="ArchivingDatabase">` section to the new server name.  
  
3. Save and close the BAMConfiguration.xml file.  
  
4. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
5. On a computer running BizTalk Server, browse to the following folder:  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
6. At the command prompt, type:  
  
    **bm.exe update-config -FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_UpdateArchSSIS"></a> To update server and database names in all BAM SSIS packages  
  
1. Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_DM_". To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.  
  
2. In SQL Server Business Intelligence Development Studio, create a new project. Click **File**, click **New**, and then click **Project**.  
  
3. In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**. On the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.  
  
4. In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.  
  
5. In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_DM_* packages.  
  
6. In **Package Path**, click the ellipses button.  
  
7. In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.  
  
    The package is now listed in Solution Explorer.  
  
8. In Solution Explorer, double-click the package you added in the previous step. In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 2 (BAMArchive database).  
  
9. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.  
  
    > [!NOTE]  
    >  Repeat this for data source number 3 (MSDB database).  
  
10. Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **ArchivingDatabase**, **ArchivingServer**, **PrimaryImportDatabase**, and **PrimaryImportServer** variables. You must update the values to point to the new server and database.  
  
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
  
21. Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
22. Start the IIS service.  
  
23. Start the BAM Alerts Notification service:  
  
    1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
    2.  At the command prompt, type:  
  
         **Net start NS$BamAlerts**  
  
24. Enable any BAM cube update and data maintenance SSIS packages.  
  
> [!TIP]  
>  As a good practice, you should also move the BAM_DM_* SSIS packages to the server hosting the BAMArchive database.  
  
## See Also  
 [Moving Databases](../technical-guides/moving-databases.md)