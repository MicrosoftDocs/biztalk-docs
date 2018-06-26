---
title: "Using the BTARN Management Console | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agreements, activating"
  - "activating agreements"
  - "BTARN Management Console, Scope pane"
  - "tracking"
  - "creating, trading partners"
  - "BTARN Management Console, agreements"
  - "process configuration"
  - "agreements, modifying"
  - "BTARN Management Console, home organizations"
  - "agreements, creating"
  - "BTARN Management Console, trading partners"
  - "agreements, deleting"
  - "deleting, agreements"
  - "BTARN Management Console"
  - "agreements, listing"
  - "modifying, trading partners"
  - "creating, agreements"
  - "trading partners, creating"
  - "modifying, agreements"
  - "BAM tracking"
  - "Scope pane [BTARN Management Console]"
  - "trading partners, modifying"
  - "trading partners, deleting"
  - "BTARN Management Console, process configurations"
  - "deleting, trading partners"
  - "BTARN Management Console, about BTARN Management Console"
  - "home organizations"
ms.assetid: 000ee93d-eb1d-4ff8-a9cf-0547beff027d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the BTARN Management Console
This topic describes how to administer [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] from the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.  
  
 Open the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console by clicking **Start**, pointing to **Programs**, pointing to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then clicking [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
 The scope (left) pane of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console includes all [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration nodes. The results (right) pane includes all the specific instances of whatever configuration items you have selected in the scope pane.  
  
## Operations in the Scope Pane  
 You can perform the following operations on nodes in the scope pane:  
  
- Set the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send and receive pipelines that you want to use for partner send ports. For more information, see [Setting BTARN Send and Receive Pipelines](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md).  
  
- Enable Business Activity Monitoring (BAM) tracking. For more information, see [Enabling BAM Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md).  
  
- Make sure that any newly imported configuration is visible in the console by right-clicking the configuration node in the scope pane, and then clicking **Refresh**.  
  
- View additional columns in the results pane by right-clicking the **Process Configuration Settings** or **Agreement** node in the scope pane, pointing to **View**, and then clicking **Add/Remove columns**. Move columns between the available columns and displayed columns by using the **Add or Remove** button. This command is especially useful for agreements that have many available columns that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not display by default.  
  
## Process Configurations  
 You can perform the following operations on a process configuration:  
  
-   Add a new process configuration by right-clicking the **Process Configuration Settings** scope node, pointing to **New**, and then clicking **Process Configuration**. For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
-   Edit an existing process configuration by right-clicking the process configuration in the results pane, and then clicking **Properties**, or by double-clicking the process configuration. For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
-   Delete an existing process configuration by right-clicking the process configuration in the results pane, and then clicking **Delete**.  
  
-   Create a new process configuration based on an existing process configuration by right-clicking the configuration in the results pane that you want to base the new configuration on, and then clicking **New Process Configuration from Copy**. This will display a new **Process Configuration Properties** dialog box populated with the settings of the existing configuration. Enter a new **Display code**, and then click **OK** to create the new configuration. For more information, see [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).  
  
-   Show a list of all the agreements that a process configuration is associated with by right-clicking the specific configuration in the results pane, and then clicking **Show Agreements**. This will shift the focus to the **Agreements** node in the scope pane and display the associated agreements in the results pane. You can revert to a complete list of agreements by right-clicking the **Agreements** node in the scope pane, and then clicking **Show All**.  
  
## Home Organizations  
 You can perform the following operations on a home organization:  
  
-   Add a new home organization by right-clicking the **Home Organizations** scope node, pointing to **New**, and then clicking **Home Organization**. For more information, see [Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md).  
  
-   Edit an existing home organization by right-clicking the home organization in the results pane, and then clicking **Properties**, or by double-clicking the home organization. For more information, see [Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md).  
  
-   Delete an existing home organization by right-clicking the home organization in the results pane, and then clicking **Delete**.  
  
## Partners  
 You can perform the following operations on a partner:  
  
-   Add a new partner by right-clicking the **Partners** scope node, pointing to **New**, and then clicking **Partner**. For more information, see [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
-   Edit an existing partner by right-clicking the partner in the results pane, and then clicking **Properties**, or by double-clicking the partner. For more information, see [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
-   Delete an existing partner by right-clicking the partner in the results pane, and then clicking **Delete**.  
  
## Agreements  
 You can perform the following operations on an agreement:  
  
-   Add a new agreement by right-clicking the **Agreements** scope node, pointing to **New**, and then clicking **Agreement**. For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
-   Edit an existing agreement by right-clicking the agreement in the results pane, and then clicking **Properties**, or by double-clicking the agreement. For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
-   Delete an existing agreement by right-clicking the agreement in the results pane, and then clicking **Delete**.  
  
-   Activate an agreement by right-clicking the deactivated agreement in the results pane, and then clicking **Activate**. This will enable messages associated with the agreement to be sent or received. You can also deactivate an agreement to prevent any messages associated with the agreement from being sent or received.  
  
-   Revert to a complete list of agreements, after showing a list of only the agreements that a process configuration is associated with, by right-clicking the **Agreements** node in the scope pane, and then clicking **Show All**.  
  
## See Also  
 [Setting BTARN Send and Receive Pipelines](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md)   
 [Enabling BAM Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)   
 [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)   
 [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)