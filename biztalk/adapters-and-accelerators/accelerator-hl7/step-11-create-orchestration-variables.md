---
title: "Step 11: Create Orchestration Variables | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, variables"
  - "message enrichment tutorial, orchestrations"
ms.assetid: 3d1f792d-fe74-4373-86fa-3debda55e732
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 11: Create Orchestration Variables
In this step, you create the orchestration variables for the message instances sent and received by the orchestration.  
  
 The BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) serializer expects the following part names. If you create a multipart message with any other part names, the serializer rejects the message. The message part names are:  
  
- MSHSegment  
  
- BodySegments  
  
- Z segments  
  
  The following is important information about Z segment parts:  
  
- All messages contain three parts as described above, regardless of whether a Z segment is present or not.  
  
- You use a Z segment part to contain data from the message instance, which is trailing and not defined in the schema (which also means that it is undeclared).  
  
- If there is no undeclared data, the Z segment part is blank. You do not see the Z segment parts when viewing the intermediate XML within BizTalk Mapper; however, in the BizTalk Health and Activity Tracking (HAT) tool, you see three parts to each message.  
  
### To create orchestration variables  
  
1. Click the **Orchestration View** tab next to the **Solution Explorer** tab beneath the Solutions Explorer.  
  
2. In the **Orchestration View** pane, right-click **Messages**, and then click **New Message**.  
  
3. Change the **Identifier** property in the **Properties** pane to **DoorbellInputMessage**, and then press **Enter**.  
  
4. In the **Properties** pane, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.  
  
5. Repeat steps 2 and 3 to create another message named **DoorbellOutputMessage**.  
  
6. In the **Properties** pane, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.  
  
7. In the **Orchestration View** pane, expand the **Types** node. Right-click **Multi-part Message Types**, and then click **New Multi-part Message Type**.  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] creates a new message type named **MultipartType_1** along with a new message named **MessagePart_1**.  
  
8. Click **MultipartType_1**, and in the **Properties** window, click **Identifier** and type the new name **DoorbellFinalMessageType**, and then press **Enter**.  
  
   > [!NOTE]
   >  In steps 9 through 15, you will create the parts of the multipart message. The order in which you create the parts of a multipart message is important. Always create the header, then the body, then the Z segment.  
  
   > [!NOTE]
   >  Once you have created and named the message parts, do not rename them. If necessary, delete the old body part, and create a new body part with a new name.  
  
9. In the **Types** window, under **Multi-part Message Types**, expand **DoorbellFinalMessageType**, and then click **MessagePart_1**. In the **Properties** pane, enter **MSHSegment** for **Identifier**, and then press **Enter**. In the drop-down list for **Type**, expand **.NET Classes**, and then click \<**Select from referenced assemblies\>**.  
  
10. In the **Select Artifact Type** dialog box, in the left pane, click **System.Xml**. In the right pane, click **XmlDocument**, and then click **OK**.  
  
11. In the Orchestration View window, right-click **DoorbellFinalMessageType**, and then click **New Message Part** to create MessagePart_1.  
  
12. In the **Properties** window, enter **BodySegments** for **Identifier**, and then press **Enter**. In the drop-down list for **Type**, expand **Schemas**, and then select **BTAHL7Schemas.ADT_A04_22_GLO_DEF** from the drop-down list.  
  
13. Set the **Message Body Part** property to **True**.  
  
14. In the **Orchestration View** window, right-click **DoorbellFinalMessageType**, and then click **New Message Part**.  
  
15. In the **Properties** pane, enter **ZSegments** for **Identifier**, and then press **Enter**. Click **Type**, expand **.NET Classes**, and then click **System.String** from the drop-down list.  
  
    > [!NOTE]
    >  You use **System.String** for the Z segments message part, because a Z segment contains string data that does not need to conform to a schema.  
  
16. In the **Orchestration View** window, right-click **Messages**, and then click **New Message**.  
  
17. In the **Properties** window, enter **DoorbellFinalMessage** for **Identifier**, and then press **Enter**. In the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.  
  
18. In the **Orchestration View** window, right-click **Variables**, and then click **New Variable**.  
  
19. In the **Properties** pane, enter **HeaderInfo** for **Identifier**, then press **Enter**. In the drop-down list for **Type**, double-click \<**.NET Class\>**.  
  
20. In the **Select Artifact Type** window, in the left pane, click **System.Xml**. In the right pane, click **XmlDocument**, and then click **OK**.  
  
21. In the **File** menu, click **Save All**.  
  
    Proceed to [Step 12: Configure Orchestration Shapes](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)