---
description: "Learn more about: Step 15: Configure the Send and Receive Ports"
title: "Step 15: Configure the Send and Receive Ports"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# Step 15: Configure the Send and Receive Ports
In previous steps, you created a logical send and receive port using Orchestration Designer and set the port binding to "Specify Later". In this step, you use BizTalk Explorer to finalize the port configuration by defining the physical source and destination locations and binding the physical ports to the logical ports that you created in the orchestration.  
  
## Configure the send and receive ports  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  
  
2.  Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.  
  
3.  In the Send Port Properties dialog box, in the **Name** box, type **MLLPSendPort**.  
  
4.  For **Type**, select **MLLP**.  
  
5.  Click the **Configure** button to the right of the **Type** field.  
  
6.  In the MLLP Transport Properties dialog box, for **Connection Name** enter **MLLPConnection**. For **Host** enter **localhost**. Click **OK**.  
  
7.  In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**, and then click **OK**.  
  
8.  In the Administration Console, right-click **MLLPSendPort** port, and then click **Start**.  
  
9. Expand **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Start**. If the host is already running, click **Restart**.  
  
10. Click **Orchestrations**, right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Properties**.  
  
11. In the Orchestration Properties dialog box, in the console tree, click **Bindings**.  
  
12. In the **Bindings** pane, for **Host**, select **BizTalkServerApplication**.  
  
13. For **SOAPReceivePort**, select **WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** in the **Receive Ports** column.  
  
14. For **MLLPSendPort**, select **MLLPSendPort** in the **Send Ports/Send Port Groups** column.  
  
15. Click **OK** to save the changes.  
  
## MSH 5 and MSH 6  
 The MSH 5 and MSH 6 header fields contain the destination application and facility, respectively. In Configuration Explorer, you can specify the values for each of the three components of MSH 5 and MSH 6, in cases when you want the destination information in the message to be changed. This is a likely scenario when the original message does not include party-specific information. This step is applicable in the declarative (publisher/subscriber) model. You perform this step if it is applicable in your environment. For more information about setting these values, see [Parties - BTAHL7 Configuration Explorer](parties-tab.md).  
  
 Proceed to [Step 16: Start the Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
