---
title: "Upgrade BizTalk Accelerator for HL7 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91b6747f-e560-4cf8-99b5-af0d150599bf
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Upgrade BizTalk Accelerator for HL7
Overview of the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] upgrade process. 

<a name="BKMK_BeforeUpgrade"></a>   
## Before you upgrade  

- The user running the upgrade must be a member of the BizTalk Administrators group.  

- The SQL Server (MSSQLSERVER) service must be running when you perform an upgrade.  

- Do not run a silent installation to upgrade.  

- When you upgrade, the setup program migrates the existing [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] configuration information to the newer version.  

- When you upgrade, the registry keys and databases are automatically backed up.  

- The files in the *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7 folder are updated.  

> [!IMPORTANT]
>  The upgrade does not create a new folder for the upgraded files, nor does it change the name of the existing folder.  

<a name="BKMK_UpgradePaths"></a>   
## Supported Upgrade Paths  
 The following table lists the supported [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] versions that can be upgraded. “Yes” means the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version can be upgraded. “No” means the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version cannot be upgraded. If the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version is not listed, that version cannot be upgraded.  


|                                                                                              | [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] | BizTalk Server 2013 |
|----------------------------------------------------------------------------------------------|------------------------------------------------------|-------------------------------------------------------|---------------------|
| [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2013 |                         Yes                          |                          Yes                          |         No          |
| [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2010 |                          No                          |                          Yes                          |         Yes         |

<a name="BKMK_UpgradeSteps"></a>   
## Upgrade Steps  

1. Upgrade the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].   

2. Back up the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] databases and your HL7 message schemas.  

3. Back up any files under the ***\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for HL7** folder that you have changed. For example, back up files in the SDK.  

4. Install the appropriate update for your version of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:  

   -   If upgrading from BTAHL7 2010, install **HL72010Patch.msp**.  

   -   If upgrading from BTAHL7 2013, install **HL72013Patch.msp**.  


5. Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup. See [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).  

6. Deploy the new BTAHL7V2*x*Common project.  

7. Redeploy all other assemblies.  

8. Rebuild any projects or assemblies that have a reference to one or more of the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assemblies. Using **BTSTask.exe** in \<*drive*\>:\Program Files\Microsoft BizTalk Server \<version\>, manually redeploy these projects.  

9. Restart the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] service.  

<a name="BKMK_UpgradeMulti"></a>   
## Upgrading in a Multi-server Environment  
 In a multi-server [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] environment, upgrade all [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s, and then upgrade the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] on all servers. Migrate your servers in the following order:  

-   The server hosting the BizTalk Group  

-   Each processing node  

-   The BAM portal server  

## See Also  
 [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)