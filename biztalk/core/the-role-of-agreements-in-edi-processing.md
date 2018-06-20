---
title: "The Role of Agreements in EDI Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d81b0449-6656-49f7-a781-5fd60031b3d5
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Role of Agreements in EDI Processing
An organization uses [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive EDI messages from, and send EDI messages to, one or more trading partners. The trading partners, in turn define business profiles that are business entities within an organization. How business profiles exchange messages is defined as part of trading partner agreements between two business profiles. For more information, see [Building Blocks of a Trading Partner Management Solution](../core/building-blocks-of-a-trading-partner-management-solution.md).  
  
 You create a trading partner agreement in the Trading Partner Management (TPM) user interface. The TPM screens are in the **Parties** node of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
## Configuring an Agreement for EDI Processing  
 All trading partners that will be exchanging EDI messages using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must agree upon communication parameters. After they have done this, the organization hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must create the trading partners in TPM (including a trading partner for itself), create the business profiles, and the trading partner agreement between the business profiles. As part of the trading partner agreement, you set the properties for how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message from, and send an EDI message to, the trading partner’s business profile. On their end, the other trading partners must do the same, and to exchange messages, the configurations must be compatible.  
  
 You must define the following sets of properties for EDI communications.  
  
- Trading partner properties that define general aspects of the trading partner, such as name, send ports, and the signing certificate.  
  
- Business profile properties that define the business identities.  
  
- EDI properties, as part of the trading partner agreement, that defines how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will process an incoming message from a trading partner and how it will generate an outgoing message bound to the trading partner.  
  
- AS2 properties, as part of the trading partner agreement, that defines how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform AS2 communications, both incoming and outgoing. These properties affect EDI communications only when an EDI message is sent over AS2.  
  
  > [!NOTE]
  >  The AS2 agreement and the EDI messaging agreement between the same business profiles are specified separately. The two agreements together form a partnership.  
  
  Trading partner agreement properties determine the following specific processing:  
  
- EDI envelope processing and generation  
  
- ACK processing and generation  
  
- Validation of incoming and outgoing EDI messages  
  
- Batch creation  
  
- Status reporting  
  
  For business identities, there can be specific values, such as **D-U-N-S (Dun & Bradstreet)**. Specific names have specific qualifiers, such as "01" for Duns. When a business identity name is not specific, "ZZ" is used for X12-encoded messages and "ZZZ" is used for EDIFACT-encoded messages, indicating a name mutually defined by separate entities. The value and qualifier then identifies the business profile. The name of the business identity is for informational purposes only; it is not used by the BizTalk runtime for processing.  
  
## Determining an Agreement for EDI Processing  
 Any time [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message, it attempts to determine the trading partner agreement that the message resolves to. It attempts to resolve the trading partner agreement by making a match between the message and the sender qualifier, sender identifier, receiver qualifier, and receiver identifier defined as part of the agreement. For more details on this process, see [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
 Any time [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates an EDI message to send, it attempts to determine the agreement that associates with the business profile to which the message will be sent. It attempts to resolve the agreement by making a match between the message and the agreement using any of the following:  
  
- Context property AgreementPartIdForSend  
  
- Context properties AgreementNameForSend, SenderPartyNameForSend, and ReceiverPartyNameForSend  
  
- Sender qualifiers and identifiers, and receiver qualifiers and identifiers  
  
- Send port name  
  
  For more details on this process, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
## Using EDI Global Properties  
 If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot determine the agreement for either an incoming or outgoing message, it will use the fallback agreement to process the incoming interchange or generate the outgoing interchange. The fallback agreements are set by right-clicking the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console and clicking **X12 Fallback Settings** (for X12-encoded messages) or **EDIFACT Fallback Settings** (EDIFACT-encoded messages). For more information on global properties, see [Configuring Global or Fallback Agreement Properties](../core/configuring-global-or-fallback-agreement-properties.md).  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use fallback agreement only if it cannot determine the agreement for an interchange. If an agreement has been determined, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will not use a property value from the fallback agreement for a property that has not been defined for the agreement between two trading partners.  
  
 Fallback agreements will not be used if port settings require authentication. If the port settings for a receive port require authentication (if either **Drop messages if authentication fails** or **Keep messages if authentication fails** is selected on the **General** page of the **Receive Port Properties** dialog box), an agreement is required for any interchange received by the receive port. In this case, fallback agreements are not used. If no agreement is determined for an interchange, the interchange will be treated as though authentication had failed, and will be suspended.  
  
## See Also  
 [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)   
 [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)   
 [Configuring EDI Properties](../core/configuring-edi-properties.md)   
 [Configuring Global or Fallback Agreement Properties](../core/configuring-global-or-fallback-agreement-properties.md)   
 [Known Issues with EDI Parties](../core/known-issues-with-edi-parties.md)