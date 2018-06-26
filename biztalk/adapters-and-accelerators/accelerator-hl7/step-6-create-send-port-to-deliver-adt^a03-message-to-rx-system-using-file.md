---
title: "Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter | Microsoft Docs"
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
ms.assetid: 66c4b524-c8ff-43b5-9c44-6d7bc759ae2c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter
In this step, you create the send port for the Pharmacy System (RX) using the File adapter.  

### To create the Tutorial_sendMsg_RX send port  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the **Send Port Properties** dialog box, do the following actions and then click **OK**.  


   |      Use this      |                                To do this                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      **Name**      |                       Type **Tutorial_sendMsg_RX**.                       |
   | **Transport type** |                 Select **FILE** from the drop-down list.                  |
   |   **Configure**    | Click **Configure** to open the **File Transport Properties** dialog box. |


3. In the FILE Transport Properties dialog box, do the following actions and then click **OK**.  


   |        Use this        |                                                                     To do this                                                                     |
   |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Destination folder** | Browse to **\<**<em>drive</em>**:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX**. |
   |     **File name**      |                                   Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).                                   |


4. In the **Send Port Properties** dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

5. In the left pane, select **Filters**, and then do the following actions. Click **OK** to continue.  


   |          Use this          |                                            To do this                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   | **Property** (first line)  |                       Select **BTS.MessageType** from the drop-down list.                        |
   |        **Operator**        |                              Select **!=** from the drop-down list.                              |
   |         **Value**          |                Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**.                 |
   |        **Group By**        |                              Select **OR** from the drop-down list.                              |
   | **Property** (second line) | Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list. |
   |        **Operator**        |                              Select **!=** from the drop-down list.                              |
   |         **Value**          |                Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>.**                 |
   |        **Group By**        |                             Select **AND** from the drop-down list.                              |
   | **Property** (third line)  |                                 Select **BTAHL7Schemas.MSH3_1**.                                 |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                                   Type **Tutorial_ADTSystem**.                                   |

   > [!NOTE]
   >  The first filter means that the Hospital Information System (HIS) is subscribing to a message, not an acknowledgment. The second filter means that HIS is subscribing to messages whose source is the Admissions Discharge and Transfer (ADT) System.  

   > [!NOTE]
   >  BTAHL7 drops the message at the file drop location \<*drive*\>:Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd-to-End TutorialTutorial_sendMsg_RX.  

6. Click **Apply**, and then click **OK.**  

7. In the Administration Console, click **Send Ports**, right-click **Tutorial_sendMsg_RX**, and then click **Start**.  

   Proceed to [Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md).