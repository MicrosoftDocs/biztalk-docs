---
title: "Update, repair, or uninstall BizTalk Accelerator for HL7 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2fc84d2-1262-4a6e-ae9c-488a00ab4099
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update, repair, or uninstall BizTalk Accelerator for HL7

Change, repair or uninstall the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].  
  
> [!IMPORTANT]
>  Be sure to uninstall [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] before uninstalling [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] cannot be uninstalled if [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is no longer installed.  

## Prerequisites
* Sign in using an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

* This user account must also be a member of the Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that stores the BizTalk Accelerator for HL7 data.  
    
## Update an existing installation

> [!NOTE]
>  When you modify your installation of [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], the End-to-End Tutorial does not automatically run. 
> 
> To run the tutorial and verify that the modified installation executed correctly, run the tutorial manually from the ***\<drive\>*** **\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial** folder.
  
1. Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** as an administrator 
  
2. On the welcome page, select **Next**.  
  
3. In **Program Maintenance**, select **Modify**, and then select **Next**.  
  
4. In **Custom Setup**, select the features that you want to install, clear the features you don't want, and then select **Next**.  
  
5. In the summary, select **Next**.  
  
6. Select **Install**.  
  
7. When complete, select **Finish**.  

## Repair an existing installation
The [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] Wizard repairs an installation by fixing missing or corrupt files, shortcuts, or registry entries.  
  
1. Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** as administrator.  
  
2. On the welcome page, select **Next**.  
  
3. In **Program Maintenance**, select **Repair**, and then select **Next**.  
  
4. In **Logging Service Account**, re-enter the user account, and then select **OK**.  
  
5. If prompted **The account name has been granted logon as a service right**, then select **OK** to continue.  
  
6. When ready to repair, select **Install**.  
  
7. When completed, select **Finish**. 

  
## Uninstall BTAHL7  

> [!IMPORTANT]
>  If there is a receive location or send port using the MLLP transport type, the BTAHL7 setup does not remove the MLLP adapter during the uninstall of BTAHL7. Before you uninstall, remove all receive locations or send ports using the MLLP transport. Or, change the transport type from MLLP to another type. Then, the uninstall will remove the MLLP adapter.  
      
1. Open **Programs and Features**.  
  
2. Select [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], and then select **Uninstall**.  
  
3. Select **Yes** if asked to confirm. 
  
4. When completed, select **Finish**.  
  
   > [!NOTE]
   >  BTAHL7 does not automatically uninstall [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artifacts and assemblies.  
  

  
## Troubleshooting Installation Issues  
 If the server is unable to validate whether the user is a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrator, uninstalling BTAHL7 returns the following error: 
 
 `Fatal error during uninstallation`  
  
To continue with uninstallation, do the following:  
  
1. Sign in to the server as a local administrator.  
  
2. Uninstall [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
3. Uninstall [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].  
  
## See Also  
[Install or upgrade Microsoft BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)