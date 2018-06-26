---
title: "Step 8B: Configure Party Information for the RX System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b0b34ec9-220d-4a6b-9712-54c8099b663b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8B: Configure Party Information for the RX System
In this step, you configure the party information for the RX System.  

### To configure the RX System party information  

1. In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  

2. In the Party Properties dialog box, in the **Name** box, type **Tutorial_RXSystem**.  

3. In the console tree, click **Send Ports**.  

4. In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_sendMsg_RX**, and then click **OK**.  

5. Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  

6. In the BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:  


   | Use this |                    To do this                    |
   |----------|--------------------------------------------------|
   | **MSH3** |      Type **BTAHL7** in the left text box.       |
   | **MSH5** | Type **Tutorial_RXSystem** in the left text box. |


7. Click **Save**, and then close the BTAHL7 Configuration Explorer.  

   Proceed to [Step 8C: Configure Party Information for the HI System](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md).