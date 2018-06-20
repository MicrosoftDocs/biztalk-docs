---
title: "Step 5: Create a Send Port to Deliver Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f56ad7a7-5c77-4191-a001-691e5e0652a1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Create a Send Port to Deliver Messages
In this step, you create and configure a port for sending the individual messages contained in the received batch. Later in the tutorial, you will enable fragmentation for the originating party (Tutorial_BatchSource) in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer. As a result, the BizTalk integration engine will fragment the batch into individual messages, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will send those messages over the send port that you create in this step.  

 You create this port to be static, so that it will only be associated with an MLLP adapter, and it will only send to a specific destination (the destination line-of-business application). In this tutorial, that destination is MESA_IS, as contained in MSH5 of the individual messages. You create the port with filters that restrict the port to sending messages, not acknowledgments, by filtering out messages conforming to the ACK_024_GLO_DEF schema or any static acknowledgment (ACK).  

 You configure this send port to receive ACKs from the destination, by associating the send port with a receive port named **TwoWayAckReceivePort**. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup creates this port, and the accompanying receive location of **TwoWayAckReceiveLocation**. You set the send port up to work with this port by setting **Solicit Response Enable** to **Yes** and setting the **Submit Receive Location URI** to **127.0.0.1:65535** (the settings required to accept ACKs). For more information, see [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md).  

### To create a send port to deliver messages  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, do the following:  


   |      Use this      |                              To do this                               |
   |--------------------|-----------------------------------------------------------------------|
   |      **Name**      |                      Type **Tutorial_2wayMsg**.                       |
   | **Transport type** |               Select **MLLP** from the drop-down list.                |
   |   **Configure**    | Click **Configure** to open the MLLP Transport Properties dialog box. |


3. In the MLLP Transport Properties dialog box, do the following:  


   |                 Use this                  |                                                   To do this                                                   |
   |-------------------------------------------|----------------------------------------------------------------------------------------------------------------|
   |            **Connection Name**            |                                               Type **2wayMsg**.                                                |
   |                 **Host**                  |                                              Type **localhost**.                                               |
   |                 **Port**                  |                                                Type **41000**.                                                 |
   |       **Solicit Response Enabled**        | Click the field to the right of **Solicit Response Enabled**, and then select **Yes** from the drop-down list. |
   | **Submit Receive Location (URI) for ACK** |                                            Type**127.0.0.1:65535**                                             |


4. Click **OK**.  

5. In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

6. In the console tree, click **Filters**, and then do the following:  


   |          Use this          |                                                     To do this                                                      |
   |----------------------------|---------------------------------------------------------------------------------------------------------------------|
   | **Property** (first line)  |          Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.           |
   |        **Operator**        |                                       Select **!=** from the drop-down list.                                        |
   |         **Value**          |                          Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**.                          |
   |        **Group By**        |                                       Select **AND** from the drop-down list.                                       |
   | **Property** (second line) |          Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.           |
   |        **Operator**        |                                       Select **!=** from the drop-down list.                                        |
   |         **Value**          |                          Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>.**                          |
   |        **Group By**        |                                       Select **And** from the drop-down list.                                       |
   | **Property** (third line)  | Click the field on the second line under **Property**, and then select **BTS.MessageType** from the drop-down list. |
   |        **Operator**        |                                       Select **!=** from the drop-down list.                                        |
   |         **Value**          |                                                 Type **StaticAck**.                                                 |


7. Click **Enter**. In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.  

8. In the Administration Console, click **Send Ports**, right-click **Tutorial_2wayMsg**, and then click **Start**.  

   Proceed to [Step 6: Create a Send Port to Deliver Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md).