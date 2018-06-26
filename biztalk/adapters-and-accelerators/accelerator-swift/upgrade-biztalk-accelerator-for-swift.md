---
title: "Upgrade BizTalk Accelerator for SWIFT | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ede2af21-4c7d-4f9e-b255-1ada86eda68d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Upgrade BizTalk Accelerator for SWIFT
Upgrade [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)] on BizTalk Server. 

### Before you upgrade

* The user running the upgrade must be a member of the BizTalk Server Administrators group.
* The SQL Server (MSSQLSERVER) service must be running when you perform an [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] upgrade.
* Do not run a silent installation to upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)].
* Upgrade BizTalk Server, and then upgrade [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)].
* The BizTalk Server Runtime must be installed for the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] upgrade to install its runtime components. If the BizTalk Server Runtime is not installed prior to the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] upgrade, then the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Components will not install, and the previous assemblies from the Global Assembly Cache (GAC) are removed.
* When you install [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], the MessagePack is installed. Any existing versions of the MessagePack are replaced during the upgrade.
* Upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] by running the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] installation. Setup migrates the existing [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] configuration information. 
* The upgrade may not remove any deprecated features’ folders and shortcuts.

## Supported upgrade paths  
 The following table lists the supported [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] versions that can be upgraded. “Yes” means that version can be upgraded. “No” means that version cannot be upgraded. If the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] version is not listed, that version cannot be upgraded.  


|                                                                                                       | [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] | BizTalk Server 2013 |
|-------------------------------------------------------------------------------------------------------|------------------------------------------------------|-------------------------------------------------------|---------------------|
| [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 2013 |                         Yes                          |                          Yes                          |         No          |
| [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 2010 |                          No                          |                          Yes                          |         Yes         |

## Upgrade A4SWIFT

1. Back up the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] database, and your SWIFT message schemas. The installation program upgrades the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] database.

2. Back up any files in the `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT` and `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT MessagePack` folders that you've updated.
  
3. Undeploy any projects, BizTalk artifacts, or assemblies that have references to any of the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] MessagePack assemblies.

4. In Visual Studio, manually undeploy all [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] assemblies in the following order:

* Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration
* Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas
* Microsoft.Solutions.FinancialServices.SWIFT.MrsrService
* Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.

5. Run the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] setup to upgrade.

> [!NOTE]
> When you upgrade [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], the upgrade removes access permissions for the **A4SWIFT Administrators** and **A4SWIFT Users** groups from the `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT\Service` folder.         
        
## Post-upgrade steps

1. Using [BTSTask.exe](../../core/btstask-command-line-reference.md) (%programfiles%\Microsoft BizTalk Server), manually redeploy the A4SWIFT assemblies in the following order:
2. Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas
3. Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration

     > [!NOTE]
     > You do not have to redeploy `Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas`. The installation redeploys this assembly.

     > [!IMPORTANT] 
     > Before rebuilding and redeploying your schemas project in the previous step, delete the older versions of `A4SWIFT Base Types.xsd` and `SWIFT Common Data Types.xsd` from the schema project, replace them with the Message Pack versions of those schemas, and then build and deploy the schemas project. If you do not replace these schemas, you will not be able to build and deploy the schemas project.

4. Rebuild and deploy any projects or assemblies that you used with older versions of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] or Message Pack.
5. If you've made any changes to SWIFT Message Pack schemas, make those changes in the new Message Pack schemas, and then build and deploy those schemas.
6. Undeploy any existing BRE policies that were installed with previous versions of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]. Then install and deploy the newer corresponding policies from [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] installation files. You can do this manually or by using the **BREDeployment** tool.

   > [!NOTE]
   > Even though the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] upgrade does not cause any issues with the Business Rules Engine (BRE) functionality, we recommend that you replace the previous versions of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] BRE policies with the latest Message Pack BRE policies, as some BRE policies get updated for each Message Pack.
    
7. If you customized any files in the `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT` folder, then make those same changes to the newer versions.
8. Remove **a4swift_limited** as a member of the db_denydatareader role, as follows:
    1. Open SQL Server Management Studio. In Management Studio, expand **Databases**, expand **BizTalk Accelerator for SWIFT**, and then select **Roles**.
    2. Double-click **a4swift_limited**. Select **Permissions**, and check SELECT for `Bic11` and `Bic10`. Select **OK**, and close the properties.
    3. Double-click **db_denydatareader**. In the User field, select **a4swift_limited**, and then select **Remove**. Select **OK**.

9. Run the QFERollUpDBUpdate script:

    > [!NOTE]
    > You must be a member of the **A4Swift Administrators** group to run the QFERollUpDBUpdate script.
    
   1. Open SQL Server Management Studio. In Management Studio, click New Query. 
   2. Select the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] database from the drop-down list. 
   3. In Windows Explorer, go to `%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT\Scripts`, and drag the **QFERollUpDBUpdate.sql** file onto the new query pane, and then select **Execute**.
    
    
## Upgrading in a multi-server environment

In a multi-server [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] environment, on all servers, upgrade BizTalk Server, and then upgrade [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]. Migrate your servers in the following order:

* The server hosting the BizTalk Group
* Each processing node
* The BAM portal server


## Next steps
[Configure BizTalk Accelerator for SWIFT ](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)