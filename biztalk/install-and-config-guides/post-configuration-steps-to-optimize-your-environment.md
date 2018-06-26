---
title: "Post-configuration steps to optimize your environment | Microsoft Docs"
description: Tasks to complete after you install and configure BizTalk Server, including configure the SQL Agent jobs, install EDI schemas, create hosts and host instances, and more in BizTalk Server
ms.custom: ""
ms.prod: biztalk-server
ms.date: "09/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0fef6ea-e7cc-4ea9-936d-5d638bc43feb
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Post-configuration steps to optimize your environment
Post-configuration steps to help improve performance, maintain your BizTalk environment, and install the EDI schemas.

## Disable Shared Memory protocol in SQL Server

1. Open **SQL Server Configuration Manager**.
2. Expand **SQL Server Network Configuration**, and select **Protocols for MSSQLSERVER**.
3. Right-click **Shared Memory**, and select **Disable**.
4. Select **SQL Server Services**, right-click **SQL Server (MSSQLServer)**, and select **Restart**.
5. Close **SQL Server Configuration Manager**.

## Configure the SQL Agent jobs

1. **SQL Server Management Studio**, and connect to **Database Engine**.
2. Expand **SQL Server Agent**, and expand **Jobs**. Configure the following jobs:  

    Job Name  |Description  |Why you need it  
    ---------|---------|---------
    Backup BizTalk Server | Backs up the BizTalk Server databases and the log files. When configuring the job, you determine parameters like frequency and file location.<br/><br/>The following links describe the SQL Agent job and its parameters:<br/><br/>[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)<br/>[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)|This SQL Agent job also truncates the transaction logs, which helps improve performance.<br/><br/>This job does not remove or delete backup files, including older files. To delete backup files, refer to The "Backup BizTalk Server" job fails when backup files accumulate over time in the Microsoft BizTalk Server database server.
    DTA Purge and Archive |Truncates and archives the BizTalk Server Tracking database (BizTalkDTADb). When configuring the job, you determine parameters like how many days to keep completed instances and how many to days to keep all data.<br/><br/>The following links describe the SQL Agent job and its parameters: <br/><br/>[Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)<br/>[How to Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md)|This SQL Agent job directly impacts performance by maintaining the Tracking host and purging tracking events.

## Maintain your backup files

BizTalk Server does not include any job to delete backup files. As a result, how you maintain your backup files is up to you. Many users create the sp_DeleteBackupHistoryAndFiles stored procedure, and then call this stored procedure directly in the Backup BizTalk Server job. Some users create a maintenance plan. The choice is yours. This topic lists both options.

#### Option 1: Create the sp_DeleteBackupHistoryAndFiles stored procedure

1. In SQL Server Management Studio, select the BizTalk Management database (BizTalkMgmtDb). 
2. Select **New Query**, and run the following T-SQL script to create the sp_DeleteBackupHistoryAndFiles stored procedure: 

    ```
    CREATE PROCEDURE [dbo].[sp_DeleteBackupHistoryAndFiles] @DaysToKeep smallint = null
    AS

    BEGIN
    set nocount on
    IF @DaysToKeep IS NULL OR @DaysToKeep <= 1
    RETURN
    /*
    Only delete full sets
    If a set spans a day in such a way that some items fall into the deleted group and the other does not, do not delete the set
    */

    DECLARE DeleteBackupFiles CURSOR
    FOR SELECT 'del "' + [BackupFileLocation] + '\' + [BackupFileName] + '"' FROM [adm_BackupHistory]
    WHERE  datediff( dd, [BackupDateTime], getdate() ) >= @DaysToKeep
    AND [BackupSetId] NOT IN ( SELECT [BackupSetId] FROM [dbo].[adm_BackupHistory] [h2] WHERE [h2].[BackupSetId] = [BackupSetId] AND datediff( dd, [h2].[BackupDateTime], getdate() ) < @DaysToKeep )

    DECLARE @cmd varchar(400)
    OPEN DeleteBackupFiles
    FETCH NEXT FROM DeleteBackupFiles INTO @cmd
    WHILE (@@fetch_status <> -1)
    BEGIN
        IF (@@fetch_status <> -2)
        BEGIN
            EXEC master.dbo.xp_cmdshell @cmd, NO_OUTPUT
            delete from [adm_BackupHistory] WHERE CURRENT OF DeleteBackupFiles
            print @cmd
        END
        FETCH NEXT FROM DeleteBackupFiles INTO @cmd
    END

    CLOSE DeleteBackupFiles
    DEALLOCATE DeleteBackupFiles
    END
    GO
    ```

3. Open the Backup BizTalk Server job, and select **Steps**.
4. Edit the **Clear Backup History** step so that it calls the new *sp_DeleteBackupHistoryAndFiles* stored procedure instead of the previous *sp_DeleteBackupHistory* stored procedure.
5. Select **OK** to save your changes.

#### Option 2: Create a maintenance plan

1. In SQL Server Management Studio, expand **Management**, right-click **Maintenance Plans**, and select **Maintenance Plan Wizard**.
2. Name the plan (for example, name it *Purge Backup Files*), and then select the **Change** button next to **Schedule**.
3. Choose how frequently you want to purge the backup files. These settings are completely up to you. Select **OK**, and then select **Next**.
4. Select **Maintenance Cleanup Task**, and select **Next**.
5. In the **Cleanup Task** window, go to **Search folder and delete files...**, select your backup Folder (maybe f:\BizTalkBackUps), and enter **.bak** for the File extension. You can also choose to delete files based on their age. For example, enter 3 if you want to delete files that are older than 3 weeks. Select **Next**.
6. Finish going through the wizard and enter any additional information you want. Select **Finish**.


## Install EDI schemas and more EDI AS2 configuration
 The EANCOM, EDIFACT, HIPAA, and X12 schema files are included in a self-extracting executable file named  MicrosoftEdiXSDTemplates.exe. To create EDI solutions, extract these files, and deploy with your projects. To install and extract these files:  

1. Run the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] installation, and install the **Developer Tools and SDK** component. This component  downloads the MicrosoftEdiXSDTemplates.exe EDI schema file to the \XSD_Schema\EDI folder.  

   > [!NOTE]
   > If you upgrade [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], the MicrosoftEdiXSDTemplates.exe file in your installation is replaced with the new MicrosoftEdiXSDTemplates.exe file associated with the upgrade. If you need the previous the schemas, then back up the previous MicrosoftEdiXSDTemplates.exe file.  
   > 
   > [!NOTE]
   > If you upgrade message schemas when you upgrade [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to a later build, you may encounter issues using the updated schemas, or you may have to perform additional updating steps. See the "Considerations for updating schemas" section in [Important Considerations for Updating Applications](../core/important-considerations-for-updating-applications.md)

2. Go  to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\XSD_Schema\EDI, and double-click MicrosoftEdiXSDTemplates.exe.  

3. Extract the schemas to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\XSD_Schema\EDI. When you extract the schemas, they are stored in EANCOM, EDIFACT, HIPAA, and X12 folders.  

#### Add a reference to the BizTalk Server EDI application  
 EDI schemas, pipelines, and orchestrations are deployed in the **BizTalk EDI Application**. To use any other application as an EDI application, add a reference to the **BizTalk EDI Application**. Steps:  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand  **Applications**. Right-click the application that you want to use for EDI (such as *BizTalk Application 1*), select **Add**, and then select **References**.  

2. Select **BizTalk EDI Application**, and select **OK** to save your changes.  

> [!TIP]
>  To see references to other applications, right-click any application, and select **Properties**. Select **References**. You can also add new references, and remove existing references.  

> [!NOTE]
>  Do not add custom artifacts to the BizTalk EDI Application. It's best to leave this application as-is.  

#### Start batch orchestrations  
 If you enable a party to receive and/or send EDI batches, then start the batching orchestrations. These orchestrations are not started by the installation wizard or the configuration wizard. Steps:  

1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk EDI Application**, and select**Orchestrations**.  

2. Right-click each of the following orchestrations, and select **Start**:  

   -   Microsoft.BizTalk.Edi.BatchSuspendOrchestration.BatchElementSuspendService (assembly: Microsoft.BizTalk.Edi.BatchingOrchestration.dll)  

   -   Microsoft.BizTalk.Edi.BatchingOrchestration.BatchingService (assembly: Microsoft.BizTalk.Edi.BatchingOrchestration.dll)  

   -   Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService (assembly: Microsoft.BizTalk.Edi.RoutingOrchestration.dll)  

> [!NOTE]
>  The EDI batching orchestrations should only be started if you receive and/or send EDI batches. Starting them when the system is not receiving or sending EDI batches could affect system performance.  

#### Migrate EDI artifacts from a previous BizTalk version  
 The way trading partners are managed in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] was updated in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 and newer versions. In the previous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions, a party was created only for the trading partner, and not for the partner hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 and newer, a party must be created for all the trading partners, including the partner hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In previous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions, the encoding (X12 and EDIFACT) and transport (AS2) protocol properties are defined at the party level. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 and newer versions, these properties are defined through agreements.  

 To migrate party data from previous versions, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes a Party Migration Tool. Consider the following migration paths:  


| [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Version  |                                                                                                                                                                                                                                                                                                                                     Migration Path                                                                                                                                                                                                                                                                                                                                      |
|---------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]**       | Upgrade to BizTalk Server 2009. Then, use the Party Migration Tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 to migrate to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.<br /><br /> **Or**, use the Party Migration Tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 to migrate to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010. Then, upgrade to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2. |
| **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009** |                                                                                                                                                                                                           Use the Party Migration Tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 to migrate directly to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.                                                                                                                                                                                                            |
| **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010** |                                                                                                                                                                                                                                                                                       Upgrade to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.                                                                                                                                                                                                                                                                                       |

 The Party Migration Tool is available on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] media under the \PartyMigrationTool folder.  


## Install BizTalk Health Monitor (BHM)

BizTalk Health Monitor provides a dashboard to create and view MessageBox Viewer reports, create custom queries, run Terminator tasks, monitor multiple BizTalk environments, and more. If you are responsible for a BizTalk envrionment, we suggest you install and use this tool to check the health of your BizTalk environment, and also maintain it.

Key links:

[Download BHM](https://www.microsoft.com/download/details.aspx?id=43716)  
[Install BHM](http://social.technet.microsoft.com/wiki/contents/articles/26466.biztalk-server-how-to-install-the-new-biztalk-health-monitor-snap-in.aspx)  
[BHM Official Blog](https://blogs.msdn.microsoft.com/biztalkhealthmonitor/)

## Create your hosts and host instances
It is recommended to separate some key tasks into separate hosts. For example, always create a separate host that is dedicated to only tracking. Create another host/host instance that focuses on receiving messages, another host/host instance for sending messages, and another host/host instance for orchestration. 

There are many recommendations in this area. Here are a few to get you started: 

[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)  
[Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md)  
[Best Practices: Create and Configure BizTalk Server Host and Host](http://social.technet.microsoft.com/wiki/contents/articles/19701.biztalk-server-best-practices-create-and-configure-biztalk-server-host-and-host-instances.aspx)  
[Running Orchestrations in Multiple Hosts on the Same Computer](http://social.technet.microsoft.com/wiki/contents/articles/31183.biztalk-server-running-orchestrations-in-multiple-hosts-on-the-same-computer.aspx)  
[PowerShell to Create and Configure BizTalk Server Host, Host Instances and Handlers](https://gallery.technet.microsoft.com/PowerShell-to-Configure-43d77916)  
[BizTalk Server Resources on the TechNet Wiki](http://social.technet.microsoft.com/wiki/contents/articles/2240.biztalk-server-resources-on-the-technet-wiki.aspx)
