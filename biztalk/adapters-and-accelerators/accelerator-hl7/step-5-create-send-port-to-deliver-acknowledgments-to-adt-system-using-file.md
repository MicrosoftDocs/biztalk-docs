---
title: "Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "end-to-end tutorial, send ports"
  - "send ports, acknowledgements"
  - "creating, send ports"
  - "acknowledgements, send ports"
  - "send ports, creating"
ms.assetid: 565a2adf-fd86-46e3-8035-7e4748aefffc
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter
In this step, you create the send port to generate acknowledgments using the File adapter.  

### To create the Tutorial_sendAck_ADT send port  

1. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, create the \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT folder.  

2. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

3. In the Send Port Properties dialog box, do the following:  


   |      Use this      |                                To do this                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      **Name**      |                      Type **Tutorial_sendAck_ADT**.                       |
   | **Transport type** |                 Select **FILE** from the drop-down list.                  |
   |   **Configure**    | Click **Configure** to open the **File Transport Properties** dialog box. |


4. In the FILE Transport Properties dialog box, do the following and then click **OK**.  


   |        Use this        |                                                                     To do this                                                                      |
   |------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Destination folder** | Browse to **\<**<em>drive</em>**:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT**. |
   |     **File name**      |                                   Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).                                    |


5. In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

6. In the left pane, click **Filters**, and then do the following:  

   > [!NOTE]
   >  The first filter means that you are subscribing for the acknowledgment message. The second filter means that you are subscribing to the acknowledgment that is destined for the publisher Tutorial_ADTSystem.  

    Click **OK** when you are ready to continue.  


   |          Use this          |                                            To do this                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   |        **Property**        | Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list. |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**.                 |
   |        **Group By**        |                              Select **OR** from the drop-down list.                              |
   | **Property (second line)** | Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list. |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>.**                 |
   |        **Group By**        |                             Select **AND** from the drop-down list.                              |
   |        **Property**        |     Under the first property, click the blank box, and then select **BTAHL7Schemas.MSH5_1**.     |
   |        **Operator**        |                              Select **==** from the drop-down list.                              |
   |         **Value**          |                                   Type **Tutorial_ADTSystem**.                                   |

   > [!NOTE]
   >  For the send port Tutorial_sendAck_ADT, BTAHL7 drops the acknowledgments at the file drop location \<*drive*\>:Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd-to-End TutorialTutorial_sendAck_ADT.  

7. Click **Apply**, and then click **OK.**  

8. In the Administration Console, click **Send Ports**, right-click **Tutorial_sendAck_ADT**, and then click **Start**.  

   Proceed to [Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md).