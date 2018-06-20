---
title: "Working with Failed Message Subscriptions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "failed messages, subscriptions"
  - "failed messages, developing"
  - "developing, failed message subscriptions"
ms.assetid: 8dee0aa8-53bf-40be-866b-f1b83960dc99
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with Failed Message Subscriptions
When the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] disassembler processes (parses and validates) a message, it promotes properties for that message. These promoted properties provide information about the correctness and validity of the message, as well as batch-related information if A4SWIFT received the message as part of an inbound batch. For a complete list of these properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
 Unlike native BizTalk Disassemblers, the A4SWIFT disassembler does not suspend a message when processing produces errors or failures. Instead, it publishes the failed message to the MessageBox database just as it would a valid message. As a result, failed messages can carry error details into the MessageBox database. You can retrieve the message from the MessageBox database, handle and repair the message, and even resubmit the message back into the MessageBox database. You would not be able to perform most of these tasks if the message was actually *suspended*.  
  
 You can identify a message that A4SWIFT has published to the MessageBox database as failed or erroneous by its promoted properties. When processing a failed message, the SWIFT disassembler populates and promotes the **A4SWIFT_Failed** property, and one or more of the other following properties, before publishing the message to the MessageBox database:  
  
- **A4SWIFT_ParseErrors** indicates the number of parsing errors (such as malformed data) encountered during processing.  
  
- **A4SWIFT_XmlValidationErrors** indicates the number of XML validation errors (such as invalid data or incorrect type with respect to the schema) encountered during processing.  
  
- **A4SWIFT_BreValidationErrors** indicates the number of Business Rule Engine (BRE) validation errors (such as data that breaks a SWIFT network rule) encountered during processing.  
  
- **A4SWIFT_Failed** is **true** when the count of any the above properties is greater than zero, or **false** when the count is equal to zero.  
  
  These properties are all part of the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property namespace. For more information about these and other promoted properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
  To catch or retrieve failed messages, you need to create filter expressions (subscriptions) for send ports or orchestration receive shapes that include some of the properties listed above, as **AND** clauses of the expression.  
  
  For example, to subscribe to all failed messages, you add the following clause (as an **AND** clause if there are other clauses):  
  
  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property.A4SWIFT_Failed == **true**  
  
  To subscribe to messages with only parse failures, you add the following clauses together:  
  
  **AND** [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property.A4SWIFT_Failed == **true**,**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property.A4SWIFT_XmlValidationErrors == 0,**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property.A4SWIFT_BreValidationErrors == 0;  
  
  Conversely, for send ports or orchestrations designed to handle only valid messages, include "**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property.A4SWIFT_Failed == **false**" as a clause in their filter expressions.  
  
> [!NOTE]
>  If subscriptions overlap, A4SWIFT will fulfill all subscriptions. That is, if more than one service (send port or orchestration) has filter expressions fulfilled by a particular message, all such services will receive the same message. For example, if a send port subscribes to all failed messages and an orchestration subscribes to only messages with parse failures, both subscriptions will be satisfied when A4SWIFT encounters parse errors when processing a message. Be sure to eliminate unwanted overlaps in subscriptions across services.  
> 
> [!NOTE]
>  If A4SWIFT receives and processes a message, and publishes that message to the MessageBox database, but the message does not satisfy any subscription, A4SWIFT will suspend the message with a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] error indicating a lack of subscribers. For example, if you have a service subscribing to all messages "A4SWIFT_Failed == false", but no services subscribe to messages where "A4SWIFT_Failed == true", then messages that fail parsing or validation will indeed be suspended due to a lack of subscribers. This scenario actually enables you to mimic traditional suspension of failed messages. Be sure to subscribe to all messages that you do not want to have suspended. See BizTalk Server Help for additional details about MessageBox database subscriptions, send ports, orchestrations, and filter expressions.  
  
 This section contains:  
  
-   [Failed Messages and ErrorCollection Objects](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)