---
title: "Known Issues with EDI Batching | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 510ac82b-8a02-4135-87b7-0a5f288f5317
caps.latest.revision: 38
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI Batching
This topic describes known issues with batching in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## Subdocument Splitting Was Not Performed Even Though the Subdocument Annotation Was Set to Yes  
 **Symptom**  
  
 A HIPAA interchange was not split into subdocuments even though the subdocument_creation_break annotation within the HIPAA schema for that interchange was set to "Yes."  
  
 **Possible Cause**  
  
- The Inbound batch processing option for the sending party was set to "Preserve Interchange." A HIPAA document will not be split into subdocuments if this is the case, even though the subdocument_creation_break annotation within the HIPAA schema is set to "Yes."  
  
- The subdocument_break annotation was set to “Yes”, but the subdocument_creation_break annotation was not set to “Yes”.  
  
  **Resolution**  
  
- In the **Validation and ACK Generation Settings** page of the **EDI Properties** dialog box for the sending party, set the **Inbound batch processing** option property to either **Split Interchange as Transaction Sets – suspend Transaction Sets on Error** or **Split Interchange as Transaction Sets – suspend Interchange on Error**.  
  
- A HIPAA document will not be split into subdocuments unless the subdocument_creation_break annotation is set to “Yes.”  
  
## Validation of a Batch May Fail if Batch Configuration Settings Are Changed While the Batch Orchestration Is Activated  
 If you change batch configuration settings while the batching orchestration is processing a batch, the new configuration settings will not be picked up for that batch. This can result in validation errors in the send pipeline.  
  
 These settings are in the Batches page of the EDI Properties dialog box.  
  
 To resolve this issue, restart the host instance(s) associated with the batching orchestration(s). This will cause the change to the batch configuration settings to take place immediately.  
  
## The BatchControlMessageRecvLoc Receive Location Can Only Run on a 32-Bit Computer or in WOW on a 64-Bit Computer  
 SQL adapters only work on 32-bit computers or when running under the WOW64 emulator on 64-bit computers. As a result, the BatchControlMessageRecvLoc receive location, which is installed by the setup program and uses the SQL adapter, will only work on a 32-bit computer or when running under WOW on a 64-bit computer. This receive location is required for batch processing.  
  
 When running the BatchControlMessageRecvLoc receive location under WOW on a 64-bit computer, you should run the batching orchestrations in a different host. If they are run on the same host as the receive location, the batching orchestrations would also run under WOW, and you would lose the advantages of running on a 64-bit computer.  
  
## A Batch Can Be Picked Up By an Unintended Send Port  
 When the batching orchestration publishes an interchange, it promotes two properties: ToBeBatched = False and DestinationPartyName = \<*PartyName*\>. A send port subscribing to either or both of these properties can pick up these batched interchanges. Make sure that a send port's filters are configured such that the send port picks up those batched interchanges that it is intended to pick up.  
  
## A Batch Element Count Greater Than the Required Number of Transaction Sets for a Batch May Not Prompt Batch Release  
 If the batch release criteria is based upon the number of transaction sets per group or interchange, a batch may not be released even though the batch element count is greater than the number of transaction sets required for a batch to be released. This can happen if you enable acknowledgments, and set the batch filter criteria to add those acknowledgments to the batch. In this instance, the number of batch elements in the group (or interchange) will be greater than the number of transaction sets per group (or interchange). In that instance, a batch will not be released if the number of transaction sets per group (or interchange) is smaller than the number required for batch release, but at the same time the number of batch elements could be greater than the number of transaction sets required for batch release.  
  
## No Batch Elements Were Saved When Start Was Clicked  
 **Symptom**  
  
 When **Start** was clicked in the Batches page for a party, no messages were collected for the batch.  
  
 **Possible Cause**  
  
 The datetime at which **Start** was clicked was earlier than the datetime entered in the **Activation** section. As a result, the orchestration instance was activated, but no messages were collected for the batch. For more information, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).  
  
 **Resolution**  
  
 Click **Stop** in the Batches page for the batch configuration experiencing this problem. Set the **Activation** to either **Start immediately** or enter a datetime earlier than the current time, and then click **Start**. When you are prompted to reset the **Start** datetime to the current time, click **OK**. BizTalk Server will start to collect messages for a batch at that point.  
  
## The Number of Bytes in an EDIFACT Batch May Depend Upon the Character Set Used  
 Characters in some EDIFACT character sets may be double-byte characters, whereas in other EDIFACT character sets they may be single-byte characters. Because of this, when you set the release criteria for batches based upon the number of characters in the interchange, the number of bytes in the interchange may differ depending on the character set used.  
  
## The Characters "<" and "&" Must be Represented in Their Encoded Form in the Envelope of a Batch  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support the following characters in their literal form when creating the envelope fields of a batched EDI interchange: "<" and "&".  
  
 Using either of these characters literally in the envelope fields of an outgoing batched interchange will result in a suspended message if the EdiSend pipeline is used to serialize the interchange.  
  
 If you need to use one of these characters in an envelope field of a batch, you can use the appropriate encoded value in the following table when you configure the envelope field in the BizTalk Administrator:  
  
|Character|Encoding|  
|---------------|--------------|  
|<|&lt;|  
|&|&amp;|  
  
 When you use one of these encoded forms, each character in the encoded form will be counted as an individual character when BizTalk Server validates the field for its length restriction in the Partner Agreement Manager (PAM) screens in the BizTalk Server Administration console. For example, even though the encoding "&lt;" would represent a single character "\<" in the batched EDI interchange, BizTalk Server would count this as four characters when validating against the length restriction of the particular field. This is an issue for PAM only, not for the EDI Assembler.  
  
## An Exeption Occurs During the Execution of the Upgrade Batch Orchestration  
 **Symptom**  
  
 When using a custom pipeline component that sets the EDI.DestinationPartyId property on incoming documents, you may receive an error in the Application event log stating that an exception has occurred during the execution of the upgrade batch orchestration.  
  
 **Possible Cause**  
  
 If ErrorMessage = “The batch was not found”, this error indicates that the upgrade batch orchestration was not able to successfully identify a batch for the incoming document.  
  
 **Resolution**  
  
 The upgrade batch orchestration uses the EDI.DestinationPartyId to look up the party name. The orchestration then constructs a string using the party name, EDI.EncodingType and the string “Default”, and then looks for a batch configuration with a matching batch name. If no batch configuration exists with this name, this error is logged to the Application event log and the orchestration instance is suspended.  
  
> [!NOTE]
>  For example, if the party name is Contoso and the EDI.EncodingType is X12, the orchestration will look for a batch named ‘ContosoX12Default’.  
  
 To resolve this problem, ensure that a batch exists with a name that will match the string constructed by the upgrade batch orchestration.  
  
## Messages Marked with EDI.ToBeBatched = True and EDI.DestinationParties are Suspended  
 **Symptoms**  
  
 When using a custom pipeline component to mark messages for batching by setting EDI.ToBeBatched = True and EDI.DestinationParties to a list of party IDs, the message will be suspended with a routing failure stating that there are no subscribers.  
  
 **Possible Cause**  
  
 In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], when a message should be processed by multiple batch configurations you would set the EDI.DestinationParties property to a space delimited list of party IDs. The routing orchestration is subscribed to messages with the EDI.ToBeBatched = True and EDI.DestinationParties properties, and would use the list of party IDs contained in the EDI.DestinationParties property to create a message for each ID, and pass the messages to the batching orchestration.  Determining the batch by using the party ID was used because each party configuration could have only one batch configuration.  
  
 In BizTalk Server, each party can have multiple batch configurations, so it is no longer sufficient to use only the pary ID to determine the batch configuration to use.  To indicate that a message must be processed by multiple batch configurations, the message must have the EDI.BatchIDs property set to a space delimited list of batch IDs that the message should be sent to.  
  
> [!NOTE]
>  When processing messages marked with only a single party ID using the EDI.DestinationPartyId property, the message will be processed by the upgrade batching orchestration. For more information, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).  
  
 **Resolution**  
  
 Upgrade the custom pipeline component so that it sets the EDI.BatchIDs property instead of EDI.DestinationParties.  The batch ID for a specific batch can be found on the Batches settings page of EDI properties for each party.  
  
> [!NOTE]
>  This problem does not occur if the BatchMarker pipeline component is used to mark the message for batching.  
  
## Batch Filter Refresh Timeout is Hardcoded to Fifteen Minutes  
 When modifying the batch filter criteria, it will take 15 minutes before the changes take effect. This refresh interval cannot be modified. To have the filter take effect immediately, restart the BizTalk Server host process.  
  
## The RoutingOrchestration Suspends After Reporting an Uncaught Exception  
 **Symptoms**  
  
 When processing documents that are destined for multiple batch configurations, you may receive an error in the Application Event Log from XLANG/s starting that the Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService failed due to an uncaught exception.  
  
 **Possible Cause**  
  
 This error can occur when the RoutingOrchestration attempts to send a message to the BatchingOrchestration and the BatchingOrchestration instance is not started.  
  
 **Resolution**  
  
 Ensure that the BatchingOrchestration instances are running before submitting documents to be batched.  
  
## Many Active Batches May Cause the BizTalkMsgBoxDb Logfile to Grow Large  
 **Symptoms**  
  
 After starting several batches, you may notice that the transaction log for the BizTalk message box database (BizTalkMsgBoxDb) has grown to a large size.  
  
 **Possible Cause**  
  
 This problem can occur if you have a large number of batches started with release criteria that causes a short interval between batch releases (for example, a batch that is scheduled to release every minute).  
  
 The batching orchestration instance that is created when you start a batch is a long running process that persists to the database after releasing a batch. Each time the orchestration persists, the transaction log will grow due to the transactions involved in persistence.  
  
> [!NOTE]
>  The batching orchestration will grow the transaction log by approximately 30kb during persistence.  
  
 **Resolution**  
  
 To resolve this problem, modify the release criteria to increase the time between batch releases. For more information, see [Configuring Batching (X12)](../core/configuring-batching-x12.md).  
  
## See Also  
 [Configuring EDI Acknowledgments](../core/configuring-edi-acknowledgments.md)   
 [Processing Incoming Batches](../core/processing-incoming-batches.md)   
 [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md)   
 [Configuring EDI Batches](../core/configuring-edi-batches.md)