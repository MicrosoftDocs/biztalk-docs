---
title: "Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "end-to-end tutorial, send ports"
  - "creating, send ports"
  - "send ports, creating"
ms.assetid: d9e7f281-3d25-4675-a13e-0e2057f5e69a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter
In this step, you create the send port to send the message to the Hospital Information System (HIS) using the MLLP adapter.  

### To create the Tutorial_MllpSend send port  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, do the following actions:  


   |      Use this      |                                To do this                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      **Name**      |                        Type **Tutorial_MllpSend**.                        |
   | **Transport type** |                 Select **MLLP** from the drop-down list.                  |
   |   **Configure**    | Click **Configure** to open the **MLLP Transport Properties** dialog box. |


3. In the MLLP Transport Properties dialog box, do the following actions and then click **OK**.  


   |      Use this       |     To do this      |
   |---------------------|---------------------|
   | **Connection Name** | Type **1WaySend**.  |
   |      **Host**       | Type **localhost**. |
   |      **Port**       |   Type **14000**.   |


4. In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

5. In the left pane, select **Filters**, and then do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Property**|Select **BTS.ReceivePortName** from the drop-down list.|  
   |**Operator**|Select **==** from the drop-down list.|  
   |**Value**|Type **Tutorial_1WayReceive**.|  

   > [!NOTE]
   >  The port will listen to the port specified in 1WayReceive for any messages.  

6. Click **Apply**, and then click **OK.**  

7. In the Administration Console, click **Send Ports**, right-click **Tutorial_MllpSend**, and then click **Start**.  

   Proceed to [Step 8: Configure Party Information](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md).