---
title: "Setting Up CIDX eStandards Message Exchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CIDX, configuring message exchange"
ms.assetid: 90468459-cef7-436b-8c0b-3a7455a091c3
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting Up CIDX eStandards Message Exchange
This topic describes how to set up Chemical Data Exchange (CIDX) eStandards message exchange. CIDX requires that you set the following three properties:  
  
- `Standard` property in the process configuration settings to **CIDX**  
  
- `Is Single Action` property in the process configuration settings to `True`  
  
- `0A1 agreement` property in the trading partner agreement to **No 0A1**  
  
  For information about the differences between CIDX and RosettaNet, see [CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md).  
  
### To set up CIDX message exchange  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. In the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3. Right-click **Process Configuration Settings**, point to **New**, and then click **Process Configuration**.  
  
4. In the New Process Configuration Properties dialog box, on the **General** tab, for the **Standard** property, select **CIDX**.  
  
5. On the **Activity** tab, for the **Is Single Action** property, select **True**.  
  
6. Enter other process configuration settings as needed. For information about these settings, see the table in [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
7. Click **OK**.  
  
8. Right-click **Agreements**, point to **New**, and then click **Agreement**.  
  
9. On the **General**, **Ports**, **Protocol**, and **Custom Properties** tabs, enter the values for the various settings. For information about these settings, see the table in [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
10. In the New Agreement Properties dialog box, on the **General** tab, for the **0A1 agreement** property, select **No 0A1**.  
  
11. Click **OK**.  
  
## See Also  
 [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)   
 [Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)