---
title: "Step 8B: Configure Party Information for the HI System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96338c05-1440-416e-a56a-6f5b19b55a60
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8B: Configure Party Information for the HI System
In this step, you configure the party information for the HI System.  
  
### To configure the HI System party information  
  
1. In the BizTalk Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  
  
2. In the Party Properties dialog box, in the **Name** field, type **HIS**. (The value you type in this box should match the original HL7 message instance, QRY^Q01.txt MSH5.)  
  
3. In the Console Tree, click **Send Ports**.  
  
4. In the **Send Port** pane, for **Name** in the first row, select **HIS_Send**, and then click **OK**.  
  
   Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md).