---
title: "Scheduling SQL Server Integration Services Packages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 037ae2cf-c352-4823-95df-9a723f2b5a81
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scheduling SQL Server Integration Services Packages
Users create BAM views based on data stored in an online analytical processing (OLAP) cube. The Cube Update Integration Services package refreshes the data in the cube so that OLAP views reflect the correct data.  
  
 You must run this package at least once for the OLAP views to work. For ongoing maintenance, you should schedule the package to run on a regular basis.  
  
> [!IMPORTANT]
>  If you restored the BAM Star Schema database or stopped [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] before running the Cube Update Integration Services package, you must refresh the data sources in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager or restart the OLAP service before you can run the package successfully.  
  
 You can schedule a saved package to execute at specific times, either once or at recurring intervals. For example:  
  
- Daily at midnight.  
  
- Weekly on Sunday at 06:00.  
  
- The first or last day of the month.  
  
  A scheduled package is executed by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] as a job.  
  
  For information about running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages, see [http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738).  
  
> [!NOTE]
>  By default, logging for archiving and cubing BAM SSIS packages is turned on and is stored in the msdb database. Overtime, this may result in a significant volume of SSIS event log data caused by large number of BAM activities or frequent execution of BAM owned SSIS packages. To resolve this, you can delete the old log entries because these entries are used primarily for debugging.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Administrators group to perform these procedures.  
  
### To run the Cube Update Integration Services package  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.  
  
3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.  
  
4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.  
  
5.  If necessary, type your user name and password.  
  
6.  Click **Connect**.  
  
7.  In the console tree, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.  
  
8.  Right-click the **BAM_AN_\<View name\>** package, and then click **Run Package**.  
  
### To run the Maintaining BAM Data Integration Services package  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.  
  
3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.  
  
4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.  
  
5.  If necessary, type your user name and password.  
  
6.  Click **Connect**.  
  
7.  In the console tree, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.  
  
8.  Right-click the **BAM_DM_\<Activity name\>** package, and then click **Run Package**.  
  
### To schedule the packages to run regularly  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Database Engine**.  
  
3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.  
  
4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.  
  
5.  If necessary, type your user name and password.  
  
6.  Click **Connect**.  
  
7.  In the console tree, expand your server, and select **SQL Server Agent**.  
  
8.  If **SQL Server Agent** is disabled, right-click **SQL Server Agent**, and then select **Start**.  
  
9. Right-click **SQL Server Agent**, and select  **New Job**.  
  
10. In the **New Job** dialog box, type a name for the job in the **Name** text box.  
  
11. In the **Select a page** window, click **Steps**, and then click **New**. This opens the **New Job Step** dialog box.  
  
12. In the **Step name** text box, type an identifying name for the step.  
  
13. In the **Type** drop-down list, select **SQL Server Integration Services Package** and in the **Package source** drop-down list, select **SSIS Package Store**.  
  
14. In the **Server** drop-down list, select the server on which you are running the job.  
  
15. Click the file selector button for the **Package** text box, select the package you are scheduling (either the **BAM_DM_\<Activity name\>** or **BAM_AN_\<View name\>** package), and then click **OK**.  
  
16. In the **Select a page** window, click **Schedules**, and then click **New**. This opens the **New Job Schedule** dialog box.  
  
17. In the **Name** text box, type a name for the schedule.  
  
18. Create your schedule using the frequency fields.  
  
19. Click **OK** to save the job.  
  
    > [!NOTE]
    >  If BAM is configured with a non-default instance of SQL Server, then the BAM_AN_POCube DTSPackage does not get scheduled/executed accurately. You need to modify the configuration file to allow packages to continue running. For more information, refer to the "Modifying the Contents of the Configuration File" section at [http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768).  
  
## See Also  
 [Managing BAM Databases](../core/managing-bam-databases.md)