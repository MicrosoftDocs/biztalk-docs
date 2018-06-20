---
title: "Step 12: Configure Orchestration Shapes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, orchestration shapes"
  - "orchestrations, shapes"
  - "message enrichment tutorial, orchestrations"
ms.assetid: 9388254b-2841-4489-838e-de913ceff151
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 12: Configure Orchestration Shapes
In this step, you complete the configuration of the orchestration shapes in order to remove the insufficient configuration smart tags. You designate **DoorbellOutputMessage** as the output of the first transform process, designating **DoorbellMap.btm** as the map used in that process. You then designate **DoorbellFinalMessage** as the output of the second transform process, and add the expression that enriches the message with additional field data.  
  
 **Prerequisite:** [KB article 941261](http://support.microsoft.com/kb/941261) must be applied before setting up Orchestration Configuration.  
  
### To configure orchestration shapes  
  
1. On the orchestration Design view surface of Visual Studio, click the **ConstructMessage_1** shape.  
  
2. In the **Properties** window, click the **Messages Constructed** property, select **DoorbellOutputMessage** from the drop-down list, and then press **Enter**.  
  
3. On the orchestration Design view surface, click the **DoorbellTransform** shape inside of the **ConstructMessage_1** shape. In the **Properties** window, click **Map Name**, and then click the ellipsis (…) button in the attribute field.  
  
4. In the Transform Configuration dialog box, select **Existing Map**. In the **Fully Qualified Map Name** drop-down list, click **BTAHL7_Project.DoorbellMap**.  
  
5. Click **Source** in the left pane.  
  
6. Click the empty box under **Variable Name** and click **DoorBellInputMessage** from the drop-down list.  
  
7. Click **Destination** in the left pane.  
  
8. Click the empty box under **Variable Name** and click **DoorbellOutputMessage** from the drop-down list.  
  
9. Click **OK** to save changes.  
  
10. On the orchestration Design view surface, click the **ConstructMessage_2** shape.  
  
11. In the **Properties** window, click **Messages Constructed**, select **DoorbellFinalMessage** from the drop-down list, and then press **Enter**.  
  
12. On the orchestration Design view surface, click the **DoorbellFinalTransform** shape inside of the **ConstructMessage_2** shape. In the **Properties** window, click **Expression**, and then click the ellipsis (…) button to open BizTalk Expression Editor.  
  
13. In BizTalk Expression Editor, click in the text field and paste the following text:  
  
    ```  
    HeaderInfo = new System.Xml.XmlDocument();   
    HeaderInfo.LoadXml("<ns0:MSH_25_GLO_DEF xmlns:ns0=\"http://microsoft.com/HealthCare/HL7/2X\">  
        <MSH><MSH.2_EncodingCharacters>^~\\&</MSH.2_EncodingCharacters><MSH.3_SendingApplication>  
        <HD.0_NamespaceId>SrcApp</HD.0_NamespaceId><HD.1_UniversalId>SrcAppUid</HD.1_UniversalId>  
        </MSH.3_SendingApplication><MSH.4_SendingFacility><HD.0_NamespaceId>srcFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>srcFacUid</HD.1_UniversalId></MSH.4_SendingFacility><MSH.5_ReceivingApplication>  
        <HD.0_NamespaceId>dstApp</HD.0_NamespaceId><HD.1_UniversalId>dstAppUid</HD.1_UniversalId>  
        </MSH.5_ReceivingApplication><MSH.6_ReceivingFacility><HD.0_NamespaceId>dstFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>dstFacUid</HD.1_UniversalId></MSH.6_ReceivingFacility><MSH.7_DateTimeOfMessage>  
        <TS.1>200307092343</TS.1></MSH.7_DateTimeOfMessage><MSH.8_Security>sec</MSH.8_Security>  
        <MSH.9_MessageType><CM_MSG.0_MessageType>ADT</CM_MSG.0_MessageType>  
        <CM_MSG.1_TriggerEvent>A04</CM_MSG.1_TriggerEvent></MSH.9_MessageType>  
        <MSH.10_MessageControlId>msgid2134</MSH.10_MessageControlId><MSH.11_ProcessingId>  
        <PT.0_ProcessingId>P</PT.0_ProcessingId></MSH.11_ProcessingId><MSH.12_VersionId>  
       <VID_0_VersionId>2.2</VID_0_VersionId></MSH.12_VersionId></MSH></ns0:MSH_25_GLO_DEF>");  
  
    DoorbellFinalMessage.MSHSegment = HeaderInfo;  
    DoorbellFinalMessage.BodySegments = DoorbellOutputMessage;  
    DoorbellFinalMessage.ZSegments = "";  
  
    DoorbellFinalMessage(BTAHL7Schemas.MSH1) = 124;   
    DoorbellFinalMessage(BTAHL7Schemas.MessageEncoding) = 65001;  
    DoorbellFinalMessage(BTAHL7Schemas.MSH2) = "^~\\&";  
    DoorbellFinalMessage(BTAHL7Schemas.ParseError) = false;   
    DoorbellFinalMessage(BTAHL7Schemas.ZPartPresent) = false;  
    DoorbellFinalMessage(BTAHL7Schemas.SegmentDelimiter2Char) = true;  
  
    ```  
  
14. Click **OK**.  
  
    > [!IMPORTANT]
    >  In the "HeaderInfo.LoadXml" expression, delete the carriage returns and spaces within the expression. The "HeaderInfo.LoadXml" statement should be on one line.  
    > 
    > [!NOTE]
    >  The first block of the preceding text is an example of a hard-coded XML header. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer requires a header segment. You can customize these header values according to the needs of your environment. The second block of the preceding text defines the three message parts required in a multipart message. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer requires a multipart message. The third block of the preceding text contains the promoted properties that the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer examines in order to serialize an XML message into an HL7 flat-file message.  
  
    Proceed to [Step 13: Create and Configure Ports](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)