---
title: "Assembling a Batched EDI Interchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18f64595-935e-4d52-9ec2-5edf7c2b9e83
caps.latest.revision: 45
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assembling a Batched EDI Interchange
To assemble individual transaction-set batch elements into an EDI interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 does the following:  
  
- Identifies batch elements for batching  
  
- Validates and buffers individual batch elements upon receipt  
  
- Retrieves specific batch elements and assembles a batched interchange when the release criteria is met  
  
  The start time for collection of individual messages to go into a batch is determined by the batch activation criteria. The time at which the batch is released is determined by the batch release criteria. For more information about these two sets of criteria, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).  
  
## Message Flow for Outgoing Batched Messages  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured to batch an outgoing message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components will perform the following series of steps to prepare the batched message for sending. This series of steps describes the case in which the EDIReceive pipeline with the BatchMarker pipeline component processes the received interchanges that contain transaction sets to be batched for sending.  
  
1. The BatchMarker pipeline component in the EDIReceive pipeline determines which messages need to be batched from the EDI batch filter settings in the party properties. (This is the only batching component that looks at the batch filter settings and acts upon them.)  
  
2. If the filter settings of only one batch configuration subscribes to a message, the BatchMarker component will promote the property `EDI.ToBeBatched = True`. This ensures that the batching orchestration will pick up the message.  
  
3. If the filter settings of more than one batch configuration match the context of a message, the BatchMarker component promotes the properties `EDI.ToBeRouted = True` and sets the `EDI.BatchIds` property to a space delimited list containing the matching batch IDs.  This ensures that the routing orchestration will subscribe to the message.  
  
   > [!NOTE]
   >  You can promote the appropriate context properties in a custom receive pipeline or a custom orchestration. The custom receive pipeline can use the BatchMarker pipeline component, or can promote the properties without using the BatchMarker pipeline component.  
  
4. The routing orchestration picks up any transaction set for which `EDI.ToBeRouted = True` and `EDI.BatchIds` is promoted, and then creates copies of the transaction set, ensuring that there is a copy for each batch ID contained in `EDI.BatchIds`. The routing orchestration sets `EDI.ToBeBatched = True` and `EDI.BatchId` is set to the batch ID of the matching batch configuration for each copy of the transaction set. This ensures that the transaction sets will be picked up by the batching orchestration for batching.  
  
5. The batching orchestration picks up all messages for which the following properties have been promoted:  
  
   - `EDI.ToBeBatched = True` and EDI.BatchId = the batch id of the batch associated with this instance of the batching orchestration.  
  
   - `EDI.ToBeBatched = True` and EDI.BatchName = the name of the configured batch and EDI.DestinationPartyName = the party name that contains the batch configuration.  
  
     When the incoming messages are processed by the EDIReceive pipeline (with the BatchMarker pipeline component), the batching orchestration will batch only X12- or EDIFACT-encoded transaction sets.  
  
   > [!NOTE]
   >  There will be one instance of the batching orchestration for each active batch configuration, each subscribing to a specific batch ID. The batch ID value is set automatically when creating a new batch configuration in the **Identification** section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.  
  
6. The batching orchestration validates each transaction set to be batched. If the transaction set fails validation, it sets the `EDI.BatchItemValidationFailure` context property to "True". The **BatchSuspend** orchestration picks up the message based upon that context property, posts error information, and then is suspended.  
  
7. When the batch release criteria has been met, the batching orchestration assembles the batch elements into a batch and creates an envelope.  
  
8. After the batching orchestration completes batching an interchange, it promotes the following properties on that interchange: EDI.DestinationPartyName = %PartyName%, EDI.BatchEncodingType = X12 or EDIFACT, and EDI.ToBeBatched = False.  
  
9. A send port picks up the batched transaction sets based on EDI.DestinationPartyName = \<PartyName\>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.  
  
## Batching Orchestration Control Messages  
 The batching orchestration is activated, terminated, or overridden by the following control messages:  
  
- **BatchActivation**: When the orchestration receives this message, an instance of the batching orchestration is created and the orchestration is active to receive batch elements (if it meets the batch activation criteria). This control message is sent by clicking the **Start** button of a batch configuration on the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.  
  
- **BatchTermination**: When the orchestration receives this message, it creates a batch from existing batch elements, publishes the message to the MessageBox, and terminates. This control message is sent by clicking the **Stop** button of a batch configuration on the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.  
  
  > [!NOTE]
  >  The orchestration is also terminated if it reaches the time specified for the **End-by** property in the **Termination** section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.  
  
- **BatchOverride**: When the orchestration receives this message, it creates a batch from existing elements, publishes the message to the MessageBox, and then waits for messages for the next batch. This control message is sent by clicking the **Override** button of a batch configuration on the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.  
  
  The batching orchestration receives the control messages via the BatchControlMessageRecvLoc receive location. The polling interval for this SQL receive location is set by default to 30 seconds, but can be changed in the **SQL Transport Properties** dialog box for the receive location. Decreasing the polling interval will ensure that the BatchControlMessageRecvLoc receive location will receive a control message soon after you perform the action that sent the control message (such as when you start the batching orchestration).  
  
  The following steps occur when you start a batch orchestration:  
  
1. When you click the **Start** button, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates a record in a table indicating which party and batch id you are activating the batch orchestration for.  
  
2. The SQL adapter associated with the BatchControlMessageRecvLoc receive location polls to see if the record exists in the database.  
  
3. If the record exists, the SQL adapter builds a control message, using information in the record.  
  
   > [!NOTE]
   >  Building the control message in this way ensures that the orchestration cannot be started by an invalid control message.  
  
4. The BatchControlMessageRecvLoc receive location receives the control message, and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] activates a batching orchestration instance.  
  
## Batch Components  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI batches XML transaction sets into EDI interchanges using the following components:  
  
- BatchMarkerReceivePipelineComponent in the EDI receive pipeline  
  
- Routing Orchestration  
  
- Batching Orchestration  
  
- Upgrade Batching Orchestration  
  
- BatchSuspend Orchestration  
  
- EDI Send Pipeline  
  
  These components are installed as DLLs when you install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2.  
  
> [!NOTE]
>  The batching components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 do not guarantee the ordering of the transaction sets in a batch.  
  
### BatchMarkerReceivePipelineComponent  
 BatchMarkerReceivePipelineComponent in the EDI receive pipeline enables the batching orchestration to pick up messages to be batched. This pipeline component is applied after the Disassembler in the EDI Receive Pipeline. The component evaluates the filter criteria set in the **Filter** section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box, and marks the transaction sets with the following context properties for processing by the routing and batching orchestrations  
  
- If a single party subscribes to a message to be batched, it promotes `ToBeBatched = True` and BatchId is set to the value of the batch ID of the matching batch configuration. This enables pickup by the batching orchestration.  
  
- If multiple batches subscribe to a message to be batched, it promotes `ToBeRouted = True`, and sets the `EDI.BatchIds` property set to a space-delimited list of batch IDs. This enables pickup by the routing orchestration.  
  
- If no subscriptions exist, it does not promote a context property. This indicates that the transaction set is not to be batched.  
  
  The pipeline component ignores messages other than XML and messages with the `ReuseEnvelope` property (preserved batches). If acknowledgments are not to be batched, the pipeline component will ignore the ACK message types (CONTRL, TA1, and 997). To optimize processing of the routing and batching orchestrations, the BatchMarkerPipelineComponent passes the message through to the MessageBox if the message context property `MessageDestination` is set to "SuspendedQueue" by the disassembler.  
  
  If you are using a custom pipeline, rather than the EDIReceive pipeline, you can use the BatchMarker component in your custom pipeline. If you are not using the EDIReceive pipeline, and are publishing messages from an orchestration, you will have to promote `ToBeBatched = True` and `BatchID` to the ID of an active batch in one of your components.  
  
### Routing Orchestration  
 The routing orchestration subscribes to any message with the context property `ToBeRouted = True` and the context property `EDI.BatchIds` set to a space-delimited list of batch IDs. This occurs when multiple batch filters subscribe to a message to be batched. The routing orchestration will make a copy of the message for each batch ID contained in `EDI.BatchIds`. It stamps each copy with two new context properties:  
  
- `EDI.BatchID`, which is set to the ID of the batch that this message is intended for.  
  
- `EDI.ToBeBatched`, which is set to True.  
  
  It then routes the copies to the MessageBox to be picked up by the batching orchestration. Each destination batch ID use a singleton instance of the same orchestration, with a filter on the specific batch ID.  
  
### Batching Orchestration  
 The batching orchestration is a stateful service that buffers batch elements (transaction sets) over a period of time, assembles them into an interchange, and then releases the interchange to the send pipeline based upon the release criteria.  
  
 After being activated, an instance of the batching orchestration can start batching messages of a particular encoding type to a given party (if the **Start** datetime has passed). At any one time there can be many instances of the batching orchestration for each party, one per active batch configuration. A single instance of the batching orchestration can release multiple batches for a single  batch configuration. After the end criteria is met, the batching orchestration instance will terminate. A new instance of the batching orchestration will need to be created manually from the Trading Partner Management (TPM) using the **Start** button.  
  
 If the batch orchestration starts before the start date time shown in the **Activation** section on the of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box, it will only receive messages that are specified in the activation range. It will not receive messages sent before the start date time.  
  
 The batching orchestration does the following:  
  
-   Subscribes to XML batch elements with the context properties `EDI.ToBeBatched = True` and `EDI.BatchId` the ID of the batch configuration, or `EDI.ToBeBatched = True` and EDI.BatchName = the name of the configured batch and EDI.DestinationPartyName = the party name that contains the batch configuration. It receives batch elements using a **Receive** action operation in a loop.  
  
    > [!NOTE]
    >  The batching orchestration does not batch transaction sets based upon the filter criteria set in the Filter section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box. It subscribes to transaction sets that have the above context properties set on them. The BatchMarker pipeline component sets and promotes those context properties based upon the filter settings in the party properties.  
  
-   Retrieves the batch configuration settings for the party identified in the `BatchId` context property.  
  
-   Validates the batch element (transaction set) based on party settings.  
  
-   If there is an error in a batch element, the batching orchestration will promoted the following property on that transaction set: `EDI.BatchItemValidationFailure = True`. The **BatchElementSuspend** orchestration subscribes to any transaction set for which this property has been promoted. This orchestration will provide detailed error information for the first error encountered in batching the interchange.  
  
-   If there is no error in a batch element, holds a reference to that batch element.  
  
-   When the appropriate control message is received or the batching release criteria is met, breaks out of the **Receive** action loop, retrieves all batch elements from the MessageBox, and assembles the interchange.  
  
-   Sets the context property `ToBeBatched = False` for the interchange and the context property DestinationPartyName = %PartyName% where %PartyName% is the name of the party for which the message is intended.  
  
    > [!NOTE]
    >  If a send port subscribes to either or both of the properties `EDI.ToBeBatched = False` and EDI.DestinationPartyName = %PartyName%, that send port can pick up the batched interchange. Make sure that a send port's filters are configured such that the send port picks up only those batched interchanges that it is intended to pick up.  
  
    > [!NOTE]
    >  Interchanges dropped by the batching orchestration into the MessageBox have only the properties `EDI.ToBeBatched = False`, EDI.DestinationPartyName = %PartyName%, and EDI.BatchEncodingType = "X12" or "EDIFACT" promoted to the context. All context properties from the original transaction sets are lost.  
  
-   For an X12-encoded interchange, applies the following properties to the envelope:  
  
    -   ISA6: Interchange Sender ID  
  
    -   ISA8: Interchange Receiver ID  
  
    -   ISA15: Usage indicator  
  
    -   ISA_Blob (written to context)  
  
-   For an EDIFACT-encoded interchange, applies the following properties to the envelope:  
  
    -   UNB2.1: Interchange Sender ID  
  
    -   UNB3.1: Interchange Recipient ID  
  
    -   UNB2.3: Address for Reverse Routing  
  
    -   UNB11: Usage indicator  
  
    -   UNA_Blob (written to context)  
  
    -   UNB_Blob (written to context)  
  
-   Delivers the batched interchange to the MessageBox for pickup by the EDI send pipeline.  
  
### UpgradeBatching Orchestration  
 The UpgradeBatching orchestration handles messages that are have the `EDI.ToBeBatched` property set to true, but do not have the `EDI.BatchID` property set.  
  
 In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], each party could have only one batch configuration.  When processing messages that had `EDI.ToBeBatched` set to true, the `EDI.DestinationPartyId` was used to determine the party and then the batch configuration was read from the agreement properties.  
  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], each party can have multiple batch configurations associated with it, so the `EDI.DestinationPartyId` does not provide enough information to determine which batch configuration should be used.  When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives messages, the `EDI.BatchId` property is used to identify which specific batch configuration should be used when processing a message.  
  
 After upgrading to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you may still have custom pipelines that use the `EDI.DestinationPartyId` property to specify the party configuration. When a message is received that has `EDI.ToBeBatched` set to true, and has `EDI.DestinationPartyID` set instead of EDI.BatchID, the UpgradeBatching orchestration attempts to determine which batch configuration should be used.  
  
 The UpgradeBatching orchestration uses the following subscription filters to subscribe to documents that are marked for batching, but do not specify a batch ID:  
  
- `EDI.ToBeBatched=True`  
  
- `EDI.EncodingType` exists  
  
- `EDI.DestinationPartyId` exists  
  
  When the orchestration receives a message, it will try to find a matching batch configuration for the message by using the party name and encoding type.  The `EDI.DestinationPartyID` property is used to determine the party name, and then the orchestration looks for a batch name that matches \<PartyName\>+\<EncodingType\>+Default.  For example if the party name is Contoso, and the value of `EDI.EncodingType` is X12, then the orchestration will look for a batch named ContosoX12Default.  
  
  If a matching batch configuration is found, the message is placed back in the message box with the following properties:  
  
- `EDI.ToBeBatched = True`  
  
- `EDI.ToBeRouted = False`  
  
- EDI.BatchId = the batch ID for the matching batch  
  
  The batching orchestration will then process the message  
  
> [!NOTE]
>  If no matching batch is found, then the following will happen:  
> 
> - The message will not be sent to the BatchSuspend orchestration.  
>   -   The UpgradeBatching orchestration instance and message will be suspended.  
>   -   An error will be logged to the event log stating that a batch was not found.  
  
### BatchSuspend Orchestration  
 The BatchSuspend orchestration handles invalid messages received by the batching orchestration. The BatchSuspend orchestration is needed because there is no direct way to suspend a message from an orchestration (in this case, the batching orchestration) without stopping the execution of the instance of the orchestration.  
  
 When an instance of the batching orchestration receives a message, it attempts to validate it. If the message fails validation, the batching orchestration creates an instance of the BatchSuspend orchestration, and sets the `EDI.BatchItemValidationFailure` context property to True. The BatchSuspend orchestration subscribes to all messages with that context property set to True. After the invalid transaction set is routed to the BatchSuspend orchestration, the BatchSuspend orchestration instance is suspended.  
  
 Detailed error information for the first error encountered is provided by the BatchSuspend orchestration.  
  
 You can create a custom orchestration to handle transaction sets that fail validation by the batching orchestration, by using the `EDI.BatchElementValidationFailure` property in a filter.  
  
### EDI Send Pipeline  
 After receiving a batched interchange from the batching orchestration, the EDI send pipeline does the following:  
  
-   For an X12-encoded interchange, the send pipeline applies the following properties to the envelope:  
  
    -   ISA2: Authorization Information  
  
    -   ISA4: Security Information  
  
    -   ISA9: Interchange Date  
  
    -   ISA10: Interchange Time  
  
    -   ISA13: Interchange Control Number  
  
    -   GS4: Date  
  
    -   GS5: Time  
  
    -   GS6: Group Control Number  
  
    -   ST2: Transaction Set Control Number  
  
-   For an EDIFACT-encoded interchange, the send pipeline applies the following properties to the envelope:  
  
    -   UNB4.1: Date  
  
    -   UNB4.2: Time  
  
    -   UNB5: Interchange Control Reference  
  
    -   UNB6.1: Recipient Reference Password  
  
    -   UNG4.1: Date  
  
    -   UNG4.2: Time  
  
    -   UNG5: Functional Group Reference  
  
    -   UNG8: Application Password  
  
-   Delivers the message via the associated adapter  
  
## See Also  
 [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md)