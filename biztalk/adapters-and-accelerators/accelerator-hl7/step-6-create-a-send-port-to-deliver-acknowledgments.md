---
title: "Step 6: Create a Send Port to Deliver Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 739b3e60-db56-46e9-a6b1-0acbe0c08f55
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Create a Send Port to Deliver Acknowledgments
In this step, you create a port to send acknowledgments back to the source of the batch.  

 You create this port to be static, so that it will only be associated with an MLLP adapter, and it will only send to a specific destination (the source of the batch). In this tutorial, the source is associated with the party Tutorial_BatchSource. This source party is contained in MSH3 of the individual messages and FHS3 and BHS3 of the original batch.  

 You create the port with filters that restrict the port to sending acknowledgments, not data messages. These filters specify a message type of ACK_024_GLO_DEF and a destination of Tutorial_BatchSource.  

 You configure this send port to receive acknowledgments from the destination, by associating the send port with a receive port named **TwoWayAckReceivePort**. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup creates this port, and the accompanying receive location of **TwoWayAckReceiveLocation**. You set the send port up to work with this port by setting **Solicit Response Enable** to **No** and setting the **Submit Receive Location URI** to **127.0.0.1:65535** (the settings required to accept ACKs). For more information, see [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md).  

### To create a send port to deliver acknowledgments  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, do the following:  


   |      Use this      |                                To do this                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      **Name**      |                        Type **Tutorial_2wayAck**.                         |
   | **Transport type** |                 Select **MLLP** from the drop-down list.                  |
   |   **Configure**    | Click **Configure** to open the **MLLP Transport Properties** dialog box. |


3. In the MLLP Transport Properties dialog box, do the following:  


   |                 Use this                  |        To do this         |
   |-------------------------------------------|---------------------------|
   |            **Connection Name**            |     Type **2wayAck**.     |
   |                 **Host**                  |    Type **localhost**.    |
   |                 **Port**                  |      Type **41002**.      |
   |       **Solicit Response Enabled**        | Keep the field as **No**. |
   | **Submit Receive Location (URI) for ACK** | Type **127.0.0.1:65535**  |


4. Click **OK**.  

5. In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

6. In the console tree, click **Filters**, and then do the following:  

   > [!NOTE]
   >  Ensure that you enter the following data exactly as shown. This data is case-sensitive.  

   |          Use this          |                                            To do this                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   | **Property** (first line)  |   Click the field under **Property**, then select **BTS.MessageType** from the drop-down list.   |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**.                 |
   |        **Group By**        |                              Select **OR** from the drop-down list.                              |
   | **Property** (second line) | Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list. |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>.**                 |
   |        **Group By**        |                             Select **And** from the drop-down list.                              |
   | **Property** (third line)  |   Click the field on the second line under **Property**, then select **BTAHL7Schemas.MSH5_1**.   |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                                  Type **Tutorial_BatchSource**.                                  |

   > [!NOTE]
   >  The first filter means that you are subscribing to the acknowledgment message. The second filter means that you want the acknowledgment that has the destination of the publisher, **Tutorial_BatchSource**.  

7. Click **Enter**. In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.  

8. In the Administration Console, click **Send Ports**, right-click **Tutorial_2wayAck**, and then select **Start**.  

   > [!NOTE]
   >  For the Tutorial_2wayAck send port to function properly, you must enable the TwoWayAckReceivePort receive location.  

9. Click **Receive Locations**. Verify that the status for the TwoWayAckReceiveLocation is enabled. If not, right-click **TwoWayAckReceiveLocation**, and then click **Enable**.  

   Proceed to [Step 7: Create and Configure a Source Party](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md).