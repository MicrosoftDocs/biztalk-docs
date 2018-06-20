---
title: "Implementing an External Batch Release Mechanism | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5633a448-cc29-4931-a3ad-206ae25c989b
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing an External Batch Release Mechanism
You can trigger the release of a batch using an external release trigger. The release could be automatically triggered by a back-end, line-of-business application upon reaching a certain threshold. This mechanism is in addition to automatically triggering the batch release by a schedule or a count of transaction sets or characters, or manually triggering the batch by clicking the **Override** button in the **Batch Configuration** page of the one-way agreement tab.  
  
 To implement an external release trigger, you need to set up a receive port and location to process the OverrideControlMessage. The receive location must use the `Edi.BatchControlMessageRecvPipeline` receive pipeline. This is the same pipeline that is used by the BatchControlMessageRecvLoc receive location that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to process manual override messages. However, BatchControlMessageRecvLoc is a SQL-type receive location, while the receive location that you set up for an external release trigger can use any adapter type.  
  
 An external batch release is triggered by an XML control message. To trigger the batch, the back-end application routes the control message to the receive location. You can modify the control message to activate, override, or terminate the batch. See the procedure below for creating the control message.  
  
 To enable the external release trigger, you must select the **External release trigger** property in the **Batch Configuration** page of the **Agreement Properties** dialog box for either X12 or EDIFACT. This property indicates that an external release message is required for batch release. The **Override** button, **Stop** button, and **Activation** range controls remain valid if the **External release trigger** property has been selected.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To create a receive location for the external batch release trigger message  
  
1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a one-way receive port. For instructions on how to create a receive port, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
  
2. Create a one-way receive location in the receive port.  
  
3. Select the transport type. You can select any type for this receive location. A common solution is to select the FILE type, and enter a folder to receive the file.  
  
4. For Receive pipeline, select `BatchControlMessageRecvPipeline`.  
  
5. Click **OK**.  
  
### To create the external batch release trigger message  
  
1. In Notepad, create a new file and name it with an .xml extension.  
  
2. Add the following to the file:  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ControlMessage xmlns="http://SQLControlMessage.IssueSelect">  
     <PAM_Control xmlns="http://SQLControlMessage.IssueSelect">  
       <DestinationParty>[Party ID]</DestinationParty>  
       <EdiMessageType>[0 for X12\HIPAA|1 for Edifact]</EdiMessageType>  
       <ActionType>EdiBatchOverride</ActionType>  
       <ActionDateTime>[yyyy-mm-ddThh:mm:ss.sss]</ActionDateTime>  
       <UsedOnce>0</UsedOnce>  
       <BatchId>[Batch ID]</BatchId>  
       <BatchName>[Batch Name]</BatchName>  
       <DestinationPartyName>[Destination Party/Partner name]</DestinationPartyName>  
       <SenderPartyName>[Sender Party/Partner name]</SenderPartyName>  
       <AgreementName>[Agreement Name]</AgreementName>  
       <ReceiverPartyNameType>[Receiver Party/Partner name]</ReceiverPartyNameType>  
       <ToBeBatched>1</ToBeBatched>  
     </PAM_Control>  
   </ControlMessage>  
   ```  
  
    Replace the values in the above excerpt as follows:  
  
   - Specify the action type. Typically, the **ActionType** must be set to **EdiBatchOverride** to override the batch settings done in the agreement. You can also set this to **EdiBatchTerminate** to terminate the batch through an external trigger.  
  
     > [!NOTE]
     >  Microsoft recommends you should not use external release trigger to activate a batch. So, you should not specify **ActionType** as **EdiBatchActivate**.  
  
   - Determine the Batch ID and Batch Name. To do so, open the **Agreement Properties** dialog box, and on the one-way agreement tab, click **Batch Configuration**. Click the tab for the batch to be overridden and enter the value of **Batch name** and **Batch ID** fields into the **BatchName** and **BatchID** nodes of the control message.  
  
   - Specify the destination party name. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, get the name of the party/partner that will be receiving the batched interchanges. Enter the name in the **ReceiverPartyNameType** node of the control message.  
  
   - Specify the sender party name. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, get the name of the party/partner that will be sending the batched interchanges. Enter the name in the **SenderPartyName** node of the control message.  
  
   - Specify the agreement name. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, in the **Agreements** section, right-click the agreement that has the batch configuration that needs be to overridden using the control message, and then click **Properties**. In the **Agreement Properties** dialog box, in the **General** tab, on the **General Properties** page, copy the value from the **Name** field in the **Agreement Parameters** section, and paste it in the **AgreementName** node of the control message.  
  
   > [!NOTE]
   >  You do not need to specify a destination party ID. The element is required in the control message only for backward compatibility.  
  
3. Save the file.  
  
### To enable the external release trigger  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, in the **Agreements** section, right-click the agreement that has the batch configuration that needs be to overridden using the control message, and then click **Properties**. In the **Agreement Properties** dialog box, on the one-way agreement tab, click **Batch Configuration**.  
  
2. In the **Batch Configuration** page, click the tab for the batch for which you want to have an external release trigger, and then under the **Release** section, select **External release trigger**.  
  
3. Click **OK**.  
  
## See Also  
 [Configuring EDI Batches](../core/configuring-edi-batches.md)   
 [How to Create a Receive Location](../core/how-to-create-a-receive-location.md)