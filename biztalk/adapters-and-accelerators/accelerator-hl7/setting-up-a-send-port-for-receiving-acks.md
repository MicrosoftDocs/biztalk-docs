---
description: "Learn more about: Setting Up a Send Port for Receiving ACKs"
title: "Setting Up a Send Port for Receiving ACKs"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Setting Up a Send Port for Receiving ACKs
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can receive acknowledgments (ACK) on a one-way send port. When you set up a new one-way send port for receiving ACKs on the same connection, you must associate that send port with a one-way receive port.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup creates a one-way receive port (called **TwoWayAckReceivePort**) and receive location (called **TwoWayAckReceiveLocation**). The receive location uses the Minimal Lower Layer Protocol (MLLP) transport type, has a URI of "127.0.0.1:65535", and uses the **BTAHL72XReceivePipeline**. These are the settings required for receiving and processing an ACK received against a message sent out by the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] send adapter, in two-way mode. This receive location should not be deleted or used for any other purposes. Never send data to this receive location. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] enables this receive location by default.  
  
 **TwoWayAckReceiveLocation**, which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Setup Wizard creates, uses the **BizTalkServerApplication** as the receive handler. However, if you choose to create a new host and use it as the receive handler for MLLP, then you must do the following to create a new **TwoWayAckReceiveLocation**:  
  
1.  Create a one-way receive port.  
  
2.  Create a one-way MLLP receive location.  
  
3.  Specify the appropriate values for the MLLP transport properties.  
  
4.  Specify the appropriate receive handler.  
  
5.  Enable the receive location.  
  
### To create a send port enabled to receive an ACK on the same socket  
  
1.  Open the BizTalk Administration Console, and then expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**. Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.  
  
2.  In the **Name** box, type the name of the send port.  
  
3.  In the **Transport** section, for **Type**, select **MLLP**.  
  
4.  Click **Configure**.  
  
5.  In the MLLP Transport Properties dialog box, type a connection name and host (for instance, **localhost**).  
  
6.  For **Solicit Response Enabled**, select **Yes**. Leave **Submit Receive Location (URI) for ACK** blank, and then click **OK**.  
  
    > [!NOTE]
    >  When you leave **Submit Receive Location** blank, BTAHL7 enters the URI for the default **TwoWayAckReceiveLocation**. You can verify that after clicking **OK** in step 6, by clicking **Configuration** again. The URI for **TwoWayAckReceiveLocation** (127.0.0.1:65535) will be entered in **Submit Receive Location (URI) for ACK**.  
  
    > [!NOTE]
    >  You must create a send port to subscribe to the ACK received, or the ACK will be seen in a suspended state, because no subscriptions were found. To subscribe to the ACK received by the send port, use filters, for example, **BTS.MessageType == \<*MessageType*\>** and **BTS.ReceivePortName == \<*ReceivePort*\>**. For static ACKs, the message type is **StaticAck**.  
  
7.  Click **OK**.  
  
## See Also  
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [Acknowledgment Error Conditions](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)
