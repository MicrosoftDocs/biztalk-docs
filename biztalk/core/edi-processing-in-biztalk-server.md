---
title: "EDI Processing in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bdc60423-24b6-4920-a870-520f575085ed
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Processing in BizTalk Server
This topic provides an overview of receive-side and send-side processing of EDI messages, and how trading partner agreements can help achieve EDI messaging.  
  
## Trading Partner Agreements for EDI Processing  
 Trading partner agreements play a key role in EDI support in BizTalk Server. Most configuration and administrative functions related to EDI processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are performed by configuring the trading partner agreements between business profiles. Agreements bring together common bi-directional message processing properties from specific business profiles of both partners. Agreements are built upon the protocol settings defined for each business profile. You implement a trading partner agreement between two business profiles by defining properties for each business profile that will be exchanging messages. You set properties for each business profile as an interchange receiver and as an interchange sender. To process an incoming message or generate an outgoing message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know the agreement that it resolves to, and the schema that applies to the message. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot determine the agreement, it will use the properties defined in the TPM interface for the fallback trading partner agreement.  
  
 There are two major sets of encoding protocol settings in TPM: one for EDIFACT properties and one for X12 properties. The two sets of properties are closely parallel. For more information about the protocol settings, see [Protocol Settings](../core/protocol-settings.md). For more information about agreements, see [Trading Partner Agreement](../core/trading-partner-agreement.md). You set the protocol settings and the trading partner agreement in the Trading Partner Management (TPM) user interface. The TPM screens are in the **Parties** node of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You do not have to be a developer to configure EDI processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 For more information about how trading partner agreements help in EDI processing, see [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md).  
  
## EDI Receive-Side Processing  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message, it processes the message in the EDI receive pipeline. The receive pipeline performs the following basic processing:  
  
- Trading partner agreement lookup and schema determination.  
  
  > [!NOTE]
  >  In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition. So, when the receive pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly. With BizTalk Server, because the party (or trading partner) is distinct from the trading partner agreement, the receive pipeline looks for the trading partner agreement specifically.  
  > 
  > [!NOTE]
  >  If all the agreements that a message resolves to are disabled, the message will be suspended. A warning is also logged in the Event log.  
  
- If a single EDI message contains multiple interchanges, splits the interchanges and processes each interchange separately (if enabled). For more information, see [Enabling the Receiving of Multiple Interchanges in a Single Message](../core/enabling-the-receiving-of-multiple-interchanges-in-a-single-message.md).  
  
- Parses each EDI interchange, converting the X12- or EDIFACT-encoded data into an XML document.  
  
- Validates the envelope and its message according to the EDI standards, the partner agreement, and the message schemas.  
  
- If the interchange is batched, either splits the batched interchange, creating an XML file for each transaction set and promoting properties required for batch processing, or preserves the interchange.  
  
- Generates an acknowledgment.  
  
- Converts the EDI envelope into context properties, and promotes other properties for EDI processing.  
  
- Promotes properties that control batch processing. This can include sending debatched transaction sets to multiple parties.  
  
  Following are some considerations that you must make while using EDI receive-side processing:  
  
- The receive location can use any type of transport type.  
  
- For more information about EDI receive-side processing, see [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md).  
  
- For more information about the specific processing performed by the EDI Disassembler in the receive pipeline, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).  
  
## EDI Batch Processing  
 If the incoming message is a batch, the EDI receive pipeline will either split the batched interchange into its constituent transaction sets, or preserve the batched interchange, depending on the configuration. The EDIReceive pipeline uses the BatchMarker pipeline component to route any interchanges that are to be batched to the batching orchestration or the routing orchestration.  
  
 After receive-side processing, transaction sets to be batched for sending will be processed by the batching orchestration. The batching orchestration will create a batch based upon filter criteria, an activation range, and release criteria.  
  
 If unbatched EDI transaction sets need to be sent to batches, a routing orchestration will process the transaction sets. A copy of the transaction set will be created for each matching batch.  
  
 For more information about the specific processing performed in batching, see [Processing Incoming Batches](../core/processing-incoming-batches.md) or [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md).  
  
## EDI Send-Side Processing  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates and sends an outgoing EDI message, it processes the message in the EDI send pipeline. The send pipeline performs the following processing:  
  
- Trading partner agreement lookup and schema determination.  
  
  > [!NOTE]
  >  In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition. So, when the send pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly. With BizTalk Server, because the party (or trading partner) is distinct from the trading partner agreement, the send pipeline looks for the trading partner agreement specifically.  
  > 
  > [!NOTE]
  >  If all the agreements that a message resolves to are disabled, the message will be suspended.  A warning is also logged in the Event log.  
  
- Serializes the EDI message, converting the XML document into X12- or EDIFACT-encoded data.  
  
- If the message data contains characters that are also used as X12 separators, the send pipeline can be configured to replace the characters in the payload with another character.  
  
- If the EDI message is a batched interchange, the send pipeline picks up the interchange from the BizTalk MessageBox after the batching orchestration has built the batch.  
  
- Validates the outgoing message.  
  
- Creates the EDI envelope according to the party properties or EDI envelope properties specified at runtime.  
  
- Processes acknowledgments received.  
  
  Following are some considerations that you must make while using EDI send-side processing:  
  
- The send port can use any type of transport.  
  
- For more information about EDI send-side processing, see [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md).  
  
- For more information about the specific processing performed in the send pipeline, see [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).  
  
## See Also  
 [EDI Support in BizTalk Server](../core/edi-support-in-biztalk-server1.md)   
 [EDI Support Issues](../core/edi-support-issues.md)   
 [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md)   
 [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)   
 [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)   
 [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md)