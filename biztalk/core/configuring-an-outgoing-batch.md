---
title: "Configuring an Outgoing Batch | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75e6f41a-0e24-47bf-9234-125791c62044
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring an Outgoing Batch
To define the way that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] batches transaction sets into an EDI interchange, you must create one or more batch configurations for an agreement. All interchanges that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] associates to that agreement and that meet the filter criteria for a batch will be batched and released according to the same release criteria for that batch configuration.  
  
 Batch configuration consists of a batch name, batch ID, filter definition, group definition, batch release criteria, and batch activation criteria. All properties and options related to batches are available on the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box. To create a batch configuration for an agreement, see [Configuring Batching (X12)](../core/configuring-batching-x12.md).  
  
> [!NOTE]
>  The document standard for the batch is ascertained from the agreement properties itself. For example, if the agreement is for X12 messages, the document standard for the batches will be X12.  
  
## Batch Categories  
 Use the drop-down list on the top-right corner of the **Batch Configuration** page to determine which batch configurations are displayed.  
  
-   **All**: Display all batch configurations.  
  
-   **Active**: Display only the active batch configurations.  
  
-   **Inactive**: Display only the inactive batch configurations.  
  
## Batch Identification  
 Batch identification contains batch name, description, batch ID, and the batching orchestration instance ID.  
  
### Batch Name  
 A batch configuration is created based on the batch name specified in **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box. Multiple batches can share the same configuration settings, but must have a unique batch name.  
  
### Batch Description  
 Batch description text box provides a description of the batch configuration.  
  
### Batch ID  
 The batch ID is generated automatically by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when a new batch configuration is created in the **Batch Configuration** page. This value is used by the BatchMarker pipeline component to flag incoming interchanges that match the batch filter of a specific batch configuration. This value is also used as a subscription filter of the batching orchestration associated with a specific batch configuration.  
  
### Orchestration Instance ID  
 The orchestration instance ID of the batch orchestration instance that is activated for this batch configuration.  
  
## Batch Filter  
 A batch is created based upon the batch filter definition applied in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box. In this filter, you determine which transaction sets or messages will be batched. You can change the value of this filter while an instance of the batch orchestration is activated. Changing the filter does not affect the batch release criteria.  
  
> [!NOTE]
>  If you change the batch filter for an active batch, it will take 15 minutes for the new filter criteria to become active as this information is cached by Biztalk Server. This refresh interval cannot be modified.  
> 
>  To force the new filter to become active immediately, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host process.  
  
 Outgoing batches can include multiple groups, but only one group per transaction type. A group can contain multiple transaction sets, but each must have the same transaction type.  
  
 Multiple batch configurations can share the same batch filter, if a document matches more than one batch filter it will be routed to all matching batches.  
  
## Group Definition  
 You determine how groups will be composed in the batch output by defining the Functional Group Headers (GS for X12 and UNG for EDIFACT) in the agreement properties. Groups are defined according to their Transaction Set Identifier (ST1) for X12 or the Message Type (UNH2.1) for EDIFACT, their version, and their target namespace. For example, an interchange can contain one group composed of one message type, and a second group composed of another message type. For more information on configuring groups, see [Configuring EDI Properties](../core/configuring-edi-properties.md).  
  
> [!NOTE]
>  The order of groups within an interchange is not defined.  
  
## Batch Release Criteria  
 Batches will be released according to criteria set in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box. Batches can be released in any of the following ways:  
  
- According to a schedule, on an hourly, daily, or weekly basis.  
  
- When a specific number of transaction sets is available for a group.  
  
- When a specific number of transaction sets is available for an interchange.  
  
- When a specific number of characters is available for batch processing.  
  
- When an external trigger is executed by an application external to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
  If you select the **Send empty batch signal** property on the **Batch Schedule** dialog box, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will send an empty batch message when the batch is scheduled to be sent even if no messages have been received by the batching orchestration.  
  
## Batch Activation Criteria  
 Batches will be released according to the batch release criteria only when the batch activation criterion has been met. To activate an instance of the orchestration, you must press the **Start** button in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box. This creates an instance of the orchestration for the batch configuration. If the **Start** button is available for clicking, an instance of the orchestration for the batch configuration is not currently activated.  
  
 After you press the **Start** button, messages will be collected for a batch only if the following are true:  
  
- The messages meet the criteria in the batch filter.  
  
- The date and time are after the datetime entered in the **Start** field.  
  
- The date and time are before the value entered in the **End by** field, or the numbers of batches processed is less than or equal to the number of occurrences in the **End after (occurrences)** field, or the **No end date** option is selected. All the three options are available under the **Termination** section.  
  
  The activation criteria are set in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.  
  
  After you have pressed the **Start** button to activate an instance of the batching orchestration, messages will not be collected for a batch until the time mentioned for the **Start** property has passed.  In the **Batch Configuration** page, if **Start immediately** is not selected and the **Start** datetime is set to a value prior to the time at which you press the **Start** button, batching will start as soon as the orchestration is active. If the activation datetime is in the future, batching will start at that time.  
  
  You can set the **Start** datetime to be a datetime in the future. However, if you click the **Start** button when the **Start** datetime is in the future, the orchestration instance will be activated, but no messages will be collected until the start datetime occurs. The BatchMarker pipeline component will not promote the appropriate properties needed to route a message to the routing orchestration or the batching orchestration until the start datetime. As a result, the message will not be batched. However, the messages will be picked up by any send port or orchestration subscribing to them as individual messages. For more information on what the BatchMarker pipeline component does, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).  
  
## Batch Termination Criteria  
 Messages will cease to be collected for a batch after the **End by** datetime or after the number of occurrences in the **End after (occurrences)** property. If you do not want the batching orchestration to be deactivated, select the **No end date** option.  
  
> [!NOTE]
>  If the **End after (occurrences)** property has been selected, empty batch signals count toward the number of occurrences required to end the batch activation range. The number of occurrences will also be incremented if the conditions that would normally lead to an empty batch signal occur (no messages have been received by the batching orchestration when the batch is scheduled to be sent), but no empty batch signal is sent because the signal is not configured.  
  
## See Also  
 [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md)