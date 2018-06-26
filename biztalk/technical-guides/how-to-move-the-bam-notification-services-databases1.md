---
title: "How to Move the BAM Notification Services Databases1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89b4938e-ea4a-48d3-80c3-eb9401e28323
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move the BAM Notification Services Databases
You can use this procedure to move the BAM Notification Services database to another server.  From an end-to-end scenario perspective, moving the BAM Notification Services database involves two major steps:  
  
-   [Moving the BAM Notification Services Database](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiMoveDB)  
  
-   [Updating References to the New BAM Notification Services Databases](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)  
  
> [!NOTE]  
>  You must move the BAM Notification Services Application (BAMAlertsApplication) database and the BAM Notification Services Instance (BAMAlertsNSMain) database together.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.  
  
##  <a name="BKMK_NotiMoveDB"></a> Moving the BAM Notification Services Database  
 Perform the steps in the following procedure to move the BAM Notification Services database.  
  
#### To move the BAM Notification Services database  
  
1. Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Notification Services database.  
  
2. Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
3. Stop the IIS service.  
  
4. Stop the BAM Alerts Notification service:  
  
   1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   2.  At the command prompt, type:  
  
        **Net stop NS$BamAlerts**  
  
5. Back up the BAM Notification Services database on the old server. For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.  
  
   > [!NOTE]  
   >  Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.  
  
6. Copy the BAM Notification Services database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.  
  
7. Restore the BAM Notification Services database on the new server. For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.  
  
   > [!NOTE]  
   >  Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.  
  
##  <a name="BKMK_NotiUpdate"></a> Updating References to the New BAM Notification Services Databases  
 After you have moved the database, you must update all the references to the new BAM Notification Services databases. The following references must be updated:  
  
- Update the BAM configuration with the new database and server names. See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig).  
  
- Re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. See [Register the Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister).  
  
###  <a name="BKMK_NotiUpdateBAMConfig"></a> To update the BAM configuration  
  
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
      >  When running this command, substitute the actual name of the server from which to get the configuration information for <servername> and substitute the actual name of the database from which to get the configuration information for <database>. For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (<http://go.microsoft.com/fwlink/?LinkId=156516>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
2. Edit the BAMConfiguration.xml file and change the **DBServer** properties in the `<DeploymentUnit Name="Alert">` section to the new server name.  
  
3. Save and close the BAMConfiguration.xml file.  
  
4. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
5. On a computer running BizTalk Server, browse to the following folder:  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**  
  
   - If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
6. At the command prompt, type:  
  
    **bm.exe update-config -FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_NotiRegister"></a> Register the Notification Services  
 After you have moved the BAM Notification Services database, you must re-register the Notification Service on all computers in the BizTalk Server group that are running Notification Services (NSservice.exe). This enables Notification Services to connect to the databases in their new location. For instructions on how to register the Notification Services, follow steps 5 through 11 at [How to Update References to the BAM Notification Services Databases](http://go.microsoft.com/fwlink/?LinkId=156684) (<http://go.microsoft.com/fwlink/?LinkId=156684>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
 Note the following while performing steps mentioned in the preceding link:  
  
-   Steps 5 and 6 in the preceding link must be performed on the servers listed in the BAM configuration XML for the following properties:  
  
    ```  
    <DeploymentUnit Name="Alert">  
      <Property Name="GeneratorServerName">Server_Name</Property>  
      <Property Name="ProviderServerName">Server_Name</Property>  
      <Property Name="DistributorServerName">Server_Name</Property>  
    </DeploymentUnit>  
  
    ```  
  
-   Step 7 through 11 must be performed on the computer that hosts the BAM portal.  
  
## See Also  
 [Moving Databases](../technical-guides/moving-databases.md)