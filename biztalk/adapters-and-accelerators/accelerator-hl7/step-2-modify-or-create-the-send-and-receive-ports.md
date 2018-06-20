---
title: "Step 2: Modify or Create the Send and Receive Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d96d02c-b75d-4d18-a127-37002c5ff138
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Modify or Create the Send and Receive Ports
You need FILE send and receive ports for the Batch In/Batch Out tutorial. If you clicked the **Launch Tutorial** button at the end of installing the Enterprise Edition of [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] created these ports for you: a send port named Tutorial_BTAHL7Drop, and a receive port named Tutorial_BTAHL7PickUp. If you have these ports, you still need to modify the send port Tutorial_BTAHL7Drop.  

 If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup did not create the send and receive ports for you, see "To create the BIBOTutorialPickup receive port" procedure in this topic, and then see "To create the BIBOTutorialDrop send port" procedure also in this topic.  

### To modify the Tutorial_BTAHL7Drop send port  

1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  

3. Click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Properties**.  

4. In the console tree, click **Filters**.  

5. In the **Filters** pane, in the second row, select **BTAHL7Schemas.MessageClass** for **Properties**, select **==** for **Operator**, and type **MessageClass2X** for **Value**. Click **Enter**.  

6. Set **Group By** on the **BTS.ReceivePortName** line to **Or**, and then click **OK**.  

7. In the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration window, expand **Platform Settings**, and expand **Host Instances**. Right-click **BizTalkServerApplication**, and then click **Restart**.  

   > [!NOTE]
   >  Only use the following procedures if you installed the Standard Edition of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], or if you did not click the **Launch Tutorial** button when you set up [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].  

### To create the Tutorial_BTAHL7Pickup receive port and location  

1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  

3. Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  

4. In the Receive Port Properties dialog box, in the **Name** box, type **Tutorial_BTAHL7PickUp**.  

5. Click **Apply** to bind the port, and then click **OK**.  

6. Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  

7. In the Select a Receive Port dialog box, click **Tutorial_BTAHL7PickUp**, and then click **OK**.  

8. In the Receive Location Properties dialog box, in the **Name** box, type **Tutorial_FileReceiveLoc**.  

9. In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.  

10. Click the **Configure** button to the right of the Type drop-down list.  

11. In the FILE Transport Properties dialog box, do the following:  


    |      Use this      |                                                                                                                                                                         To do this                                                                                                                                                                          |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Receive Folder** | Browse to **\<**<em>drive</em>**\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp**. **Note:**  This is the path to the location on the file system or public share from where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will pick up the file. |
    |   **File mask**    |                                                                                                                                                                      Type **\*.txt**.                                                                                                                                                                       |


12. Click **OK**.  

13. In the Receive Location Properties dialog box, do the following:  


    |       Use this       |                      To do this                       |
    |----------------------|-------------------------------------------------------|
    | **Receive Handler**  |    Keep **BizTalkServerApplication** as selected.     |
    | **Receive Pipeline** | Select **BTAHL72XPipelines.BTAHL72XReceivePipeline**. |


14. Click **OK**.  

15. In BizTalk Explorer, right-click **Tutorial_FileReceiveLoc**, and then click **Enable**.  

### To create the Tutorial_BTAHL7Drop send port  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, do the following:  


   |   Use this    |                                To do this                                 |
   |---------------|---------------------------------------------------------------------------|
   |   **Name**    |                       Type **Tutorial_BTAHL7Drop**.                       |
   |   **Type**    |                 Select **FILE** from the drop-down list.                  |
   | **Configure** | Click **Configure** to open the **FILE Transport Properties** dialog box. |


3. In the FILE Transport Properties dialog box, do the following:  


   |        Use this        |                                                                                                                                                                      To do this                                                                                                                                                                       |
   |------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Destination folder** | Browse to **\<**<em>drive</em>**:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop**. **Note:**  This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file. |
   |     **File name**      |                                                                                                                                          Type **%MessageID%.txt** (note that the extension is txt, not xml).                                                                                                                                          |


4. Click **OK**.  

5. In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline** from the drop-down list.  

6. In the console tree, click **Filters**, and then do the following:  


   |   Use this   |                       To do this                        |
   |--------------|---------------------------------------------------------|
   | **Property** | Select **BTS.ReceivePortName** from the drop-down list. |
   | **Operator** |              Leave **==** as the operator.              |
   |  **Value**   |             Type **Tutorial_BTAHL7PickUp**.             |
   | **Group By** |         Select **Or** from the drop-down list.          |
   | **Property** |         Select **BTAHL7Schemas.MessageClass**.          |
   | **Operator** |              Leave **==** as the operator.              |
   |  **Value**   |                Type **MessageClass2X**.                 |


7. Click **Enter**. Verify in the pane at the bottom of the dialog box that the filter expression is correct.  

8. Click **OK**.  

9. In the Administration Console, click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Start**.  

10. Expand **Platform Settings**, and then click **Host Instances**. Right-click **BizTalkServerApplication**, and then click **Restart**.  

    Proceed to [Step 3: Test the Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).