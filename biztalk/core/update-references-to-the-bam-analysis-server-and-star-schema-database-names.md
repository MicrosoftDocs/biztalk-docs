---
description: "Learn more about: How to Update References to the BAM Analysis Server and Star Schema Database Names"
title: "How to Update References to the BAM Analysis Server and Star Schema Database Names"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Update References to the BAM Analysis Server and Star Schema Database Names
If you backed up your BAMAnalysis and BAMStarSchema databases, in the event of a system or data failure you can restore that backup to a different computer and you can rename the backup.  
  
 To restore the BAM Analysis Server or BAMStarSchema databases, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md). In addition, you must update the BAM Data Transformation Services (DTS) packages with the new server name and database name.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.  
  
### To update references to the BAM Analysis Server and BAM Star Schema database name (SQL Server 2008 R2/SP1)  
  
1.  Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAMAnalysis or BAMStarSchema databases.  
  
2.  Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the databases.  
  
    1.  Click **Start**, click **Run**, and then type **services.msc**.  
  
    2.  Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.  
  
    > [!TIP]
    >  Another way to stop a service is to use the **Net Stop** command. To stop the BizTalk service using Net Stop, open a **Command Prompt** (If using Windows Server 2008 or Windows Vista, start the Command Prompt using **Run As Administrator**) and type the following: `Net Stop BTSSvc$BizTalkServerApplication` then press **Enter**.  
  
3.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Business Intelligence Development Studio**.  
  
4.  In SQL Server Business Intelligence Development Studio, create a new project. Click **File**, click **New**, and then click **Project**.  
  
5.  In the **New Project** dialog box, in **Templates**, click **Integration Services Project**, and then click **OK**.  
  
6.  In the **Integration Services Project** dialog box, in **Solution Explorer**, right-click **SSIS Packages**, and then click **Add Existing Package**.  
  
7.  In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN package.  
  
8.  In **Package Path**, click the ellipses button.  
  
9. In the **SSIS Package** dialog box, select the BAM_AN package, click **OK**, and then click **OK**.  
  
     The package is now listed in Solution Explorer.  
  
10. In **Solution Explorer**, double-click the BAM_AN package. In **Connection Managers**, double-click database number 3 (MSDB database).  
  
11. In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the MSDB server, and then click **OK**.  
  
12. Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the primary import server name and primary import database name.  
  
13. Click **File**, and then click **Save All**.  
  
14. In **Microsoft SQL Server Management Studio**, click **Connect**.  
  
15. Click **Integration Services**, double-click **Stored Packages**, click **MSDB**, right-click the BAM_AN package, and then click **Import Package**.  
  
16. In the **Import Package** dialog box, in **Package location**, select **File System**.  
  
17. In **Package Path**, navigate to your saved project, select the BAM_AN\*.dtsx file, and then click **Open**.  
  
18. Click inside the **Package Name** box to automatically populate the box.  
  
19. Click **OK**, and then click **Yes** to overwrite.  
  
20. Restart the BizTalk Application service.  
  
    1.  Click **Start**, click **Run**, and then type **services.msc**.  
  
    2.  Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.  
  
21. Enable any BAM cube update and data maintenance SSIS packages.  
  
## See Also  
 [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)
