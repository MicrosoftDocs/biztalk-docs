---
title: "Step 6: Create the Send Port for the Acknowledgment Batch | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2a0f1ee-e060-4fb9-923e-ebe8168777d9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Create the Send Port for the Acknowledgment Batch
In this step, you create a send port to deliver the acknowledgment batch that you create to the source party. This is a static one-way port with a FILE adapter type. You designate a file folder for the source (\Tutorial_BatchACKDrop), where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will drop the acknowledgment batch file. You define a filter for the port indicating what type of acknowledgment batches the ports will send. The filter specifies the source of Tutorial_BatchSource and the message type of OutboundBatch.  

### To create the send port for the acknowledgment batch  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, do the following:  


   |   Use this    |                              To do this                               |
   |---------------|-----------------------------------------------------------------------|
   |   **Name**    |                    Type **Tutorial_BatchSource**.                     |
   |   **Type**    |               Select **FILE** from the drop-down list.                |
   | **Configure** | Click **Configure** to open the FILE Transport Properties dialog box. |


3. In the FILE Transport Properties dialog box, do the following:  


   |        Use this        |                                                                                                                                                                              To do this                                                                                                                                                                               |
   |------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Destination folder** | Browse to **\<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchACKDrop**. This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file containing the acknowledgment batch. |
   |     **File name**      |                                                                                                                                            Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).                                                                                                                                             |
   |     **Copy mode**      |                                                                                                                                                                        Select **Create New**.                                                                                                                                                                         |


4. Click **OK**.  

5. In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

6. In the console tree, click **Filters**, and then do the following:  


   |   Use this   |                                                              To do this                                                              |
   |--------------|--------------------------------------------------------------------------------------------------------------------------------------|
   | **Property** | Click the field under **Property**, and then select **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** from the drop-down list. |
   | **Operator** |                                                    Leave **==** as the operator.                                                     |
   |  **Value**   |                                                    Type **Tutorial_BatchSource**.                                                    |
   | **Group By** |                                               Select **And** from the drop-down list.                                                |
   | **Property** |                                             Select **BTAHL7Schemas.BTAHL7MessageType**.                                              |
   | **Operator** |                                                    Leave **==** as the operator.                                                     |
   |  **Value**   |                                                       Type **OutboundBatch**.                                                        |


7. Press **Enter**. In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.  

8. In the BizTalk Administration Console, select **Send Ports**, right-click **Tutorial_BatchSource**, and then click **Start**.  

### To associate the send port with the source party  

1. In the BizTalk Administration Console, click **Parties**. Right-click **Tutorial_BatchSource**, and then click **Properties**.  

2. In the Party Properties dialog box, click **Send Ports** in the console tree. For **Send Ports**, select **Tutorial_BatchSource** from the drop-down list, and then click **OK**.  

   Proceed to [Step 7: Start the Orchestration and Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md).