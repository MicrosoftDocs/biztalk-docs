---
title: "Step 8A: Configure Party Information for the ADT System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0d750c2-a3c6-4571-a4e1-0d0aaaa4d400
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8A: Configure Party Information for the ADT System
In this step, you configure the party information for the ADT System.  
  
### To configure the ADT System party information  
  
1. In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  
  
2. In the Party Properties dialog box, in the **Name** box, type **Tutorial_ADTSystem**. (The value you type in this box is from the original HL7 message instance, ADT^A03.txt MSH3.)  
  
3. In the console tree, click **Send Ports**.  
  
4. In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_sendAck_ADT**, and then click **OK**.  
  
5. Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
6. In the BTAHL7 Configuration Explorer, select the **Acknowledgment** tab. For **Acknowledgment type**, select **EnhancedMode**.  
  
7. Click **Save**, and then close the BTAHL7 Configuration Explorer.  
  
   Proceed to [Step 8B: Configure Party Information for the RX System](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md).