---
title: "AS2 Processing in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0027d3db-24a5-459d-9f4e-a75f49d31d82
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Processing in BizTalk Server
This topic provides an overview of receive-side and send-side processing of AS2 messages, and how trading partner agreements can help achieve AS2 messaging.  
  
## Trading Partner Agreements for AS2 Processing  
 Trading partner agreements play a key role in AS2 support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Most configuration and administrative functions related to AS2 processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are performed by configuring the trading partner agreements between business profiles. Agreements bring together common bi-directional message processing properties from specific business profiles of both partners. Agreements are built upon the protocol settings defined for each business profile. You implement a trading partner agreement between two business profiles by defining properties for each business profile that will be exchanging messages. You set properties for each business profile as an AS2 message receiver and an AS2 message sender in the Trading Partner Management (TPM) user interface. The TPM screens are in the **Parties** node of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. You do not have to be a developer to configure AS2 processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 You can specify the AS2 properties as part of the “transport protocol settings” for a business profile or by directly specifying the AS2 settings in the trading partner agreement. For more information about the protocol settings, see [Protocol Settings](../core/protocol-settings.md). For more information about agreements, see [Trading Partner Agreement](../core/trading-partner-agreement.md).  You configure the following AS2 functionality by setting the AS2-specific properties:  
  
- Select non-repudiation storage options  
  
- Specify signing, compression, or encryption properties for outgoing messages  
  
- Request MDNs for outgoing messages  
  
- Set properties for incoming MDNs by overriding the signing, compression, encryption, and MDN properties in the header of the AS2 message.  
  
  For more information about how trading partner agreements help in AS2 processing, see [The Role of Agreements in AS2 Processing](../core/the-role-of-agreements-in-as2-processing.md).  
  
> [!NOTE]
>  There are no global properties for AS2 processing, as there are for EDI processing.  
  
## AS2 Receive-Side Processing  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an AS2 message, it processes the message in an AS2 receive pipeline. There is a pipeline for receiving an EDI message over AS2 (AS2EdiReceive), which performs both AS2 and EDI processing. Another pipeline (AS2Receive) performs only AS2 processing for non-EDI messages received over AS2.  
  
 AS2 receive-side processing includes the following:  
  
- Trading partner agreement lookup  
  
  > [!NOTE]
  >  In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition. So, when the receive pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly. With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], because the party (or trading partner) is distinct from the trading partner agreement, the receive pipeline looks for the trading partner agreement specifically.  
  > 
  > [!NOTE]
  >  If all the agreements that a message resolves to are disabled, the message will be suspended.  A warning is also logged in the Event log.  
  
- Saving copies of the message in the non-repudiation database  
  
- Check for duplicate messages  
  
- Processing messages containing multiple documents  
  
- Retrieving a documents file name from the MIME envelope  
  
- Decrypting the message  
  
- Decompressing the message  
  
- Verifying the digital signature of the message  
  
- Generating an HTTP response  
  
- Generating an MDN response  
  
  Following are some considerations that you must make while using AS2 receive-side processing:  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] returns an MDN in either synchronous or asynchronous mode. If the MDN will be returned asynchronously, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must send it over a separate send port.  
  
- When you receive a non-EDI file (not XML) over AS2, and you need to perform disassembly of the non-EDI payload, you will need to use requires a loopback mechanism with a second receive pipeline. For more information, see [Receive-Side Processing of an Incoming Non-EDI Message over AS2](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md).  
  
- The receive location can only use the HTTP adapter.  
  
- For more information about AS2 receive-side processing, see [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md).  
  
- For more information about the specific processing performed by the AS2 Disassembler in the receive pipeline, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).  
  
## AS2 Send-Side Processing  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates and sends an outgoing AS2 message, it processes the message in an AS2 send pipeline. There is a pipeline for sending an EDI message over AS2 (AS2EdiSend), which performs both AS2 and EDI processing. Another pipeline (AS2Send) performs only AS2 processing for non-EDI messages sent over AS2.  
  
 AS2 send-side processing includes the following:  
  
- Trading partner agreement lookup  
  
  > [!NOTE]
  >  In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition. So, when the send pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly. With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], because the party (or trading partner) is distinct from the trading partner agreement, the send pipeline looks for the trading partner agreement specifically.  
  > 
  > [!NOTE]
  >  If all the agreements that a message resolves to are disabled, the message will be suspended.  A warning is also logged in the Event log.  
  
- Saving copies of the message in the non-repudiation database  
  
- Applying an AS2 envelope  
  
- Sending multiple documents  
  
- Storing each documents filename as part of the MIME envelope  
  
- Signing the message  
  
  > [!NOTE]
  >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to override the default signing certificate and instead use a certificate agreed upon in the agreement. For instructions on overriding default certificate for signing outgoing messages, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).  
  
- Compressing the message  
  
- Encrypting the message  
  
- Computing an MIC value for the MDN  
  
- Processing an incoming MDN (in the case of a synchronous MDN)  
  
- Resending the message if no MDN is received  
  
  Following are some considerations that you must make while using AS2 receive-side processing:  
  
- The send port can only use the HTTP adapter.  
  
- For more information about AS2 send-side processing, see [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md).  
  
- For more information about the specific processing performed in the send pipeline, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
## See Also  
 [The Role of Agreements in AS2 Processing](../core/the-role-of-agreements-in-as2-processing.md)   
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)   
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)